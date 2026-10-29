---
name: zxc-coding-style
description: TS/TSX coding style rules - avoid complex ternaries, assign return expressions to named variables, extract multi-statement JSX event handlers into named functions. Use when writing or modifying TypeScript/React code.
---

## Guidelines

### Case 1: Conditional Expressions

Do not use "? : " for a complex condition. Complex means: any branch contains JSX, the expression spans multiple lines, or the branches are themselves nested conditionals. A single-line ternary over simple values is fine.

```tsx
// bad
let iconComponent = onClick ? (
  <button type="button" className={cls} onClick={onClick}>
    {component}
  </button>
) : (
  <div className={cls}>{component}</div>
);

// good 1
let iconComponent;
if (onClick) {
  iconComponent = (
    <button type="button" className={cls} onClick={onClick}>
      {component}
    </button>
  );
} else {
  iconComponent = <div className={cls}>{component}</div>;
}

// good 2
let iconComponent = <div className={cls}>{component}</div>;
if (onClick) {
  iconComponent = (
    <button type="button" className={cls} onClick={onClick}>
      {component}
    </button>
  );
}

// ok - single line, simple values
const label = task ? task.type : "unknown";
```

```ts
// bad
const matched = (name ?? "").toLowerCase().includes("zxc") || (content ? content.toLowerCase().includes("zxc") : false);

// good
let matched = false;
if (name) {
  matched = name.toLowerCase().includes("zxc");
} else if (content) {
  matched = content.toLowerCase().includes("zxc");
}
```

### Case 2: Return Statements

Do not return a newly constructed expression; assign it to a named variable, then return the variable. Returning an existing variable or literal directly is fine. (exclude JSX/TSX elements)

```tsx
// bad
function getTaskType(task: Task) {
  // ...
  const timestamp = xxx;
  return `${task.type} - ${timestamp}`;
}

// good
function getTaskType(task: Task) {
  // ...
  const timestamp = xxx;
  const taskType = `${task.type} - ${timestamp}`;
  return taskType;
}

// for JSX/TSX elements

// good
function SummaryLink() {
  return (
    <a href="/summary">Summary</a>
  );
}

// bad
function SummaryLink() {
  const link = <a href="/summary">Summary</a>;
  return link;
}
```

### Case 3: Event Handlers in JSX

Do not define multi-statement handlers inline in JSX; extract them into named functions defined above the return. A single-statement inline arrow is acceptable.

```tsx
// bad
function TaskList() {
  return (
    <Table
      // ...
      handleChange={({page}) => {
        setPage(page);
        if (xxx) {
          doSomething();
        }
      }}
    />
  )
}

// good
function TaskList() {
  // handler name should clearly indicate its purpose
  const handleTableChange = ({page}: {page: number}) => {
    setPage(page);
    if (xxx) {
      doSomething();
    }
  };
  return (
    <Table
      // ...
      handleChange={handleTableChange}
    />
  )
}
```
