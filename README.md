# Frappé Gantt React Wrapper

It's an updated React Component, a Wrapper for [Gantt chart library](https://github.com/frappe/gantt) from Frappé

## Install

> npm install @JacobBarr1986/frappe-gantt-react

or

> yarn add @JacobBarr1986/frappe-gantt-react

## Usage

Import it to your project

Using ES6 modules

`import { FrappeGantt } from '@toyokoh/frappe-gantt-react`

Or using CommonJS

`const { FrappeGantt,ViewMode } = require('@toyokoh/frappe-gantt-react')`

` const tasks = [ { id: "Task 1", name: "Redesign website", start: "2016-12-28", end: "2016-12-31", progress: 10, dependencies: "", }, { id: "Task 2", name: "Redesign website", start: "2016-12-28", end: "2016-12-31", progress: 20, dependencies: "Task 1", }, { id: "Task 3", name: "Redesign website", start: "2016-12-28", end: "2016-12-31", progress: 0, dependencies: "Task 2, Task 1", }, ];`

Then you can use it in your react app:

    class App extends React.Component {
        state = { mode: ViewMode.Month };
        componentDidMount() {
            console.log("test");
            setTimeout(() => {
                console.log("Setting State!");
                this.setState({ mode: ViewMode.Week });
                setTimeout(() => {
                    console.log("Setting State!");
                    this.setState({ mode: ViewMode.HalfDay });
                }, 3000);
            }, 3000);
        }

        render() {

            return (
                ...
                <div>
                    <FrappeGantt
                        tasks={tasks}
                        viewMode={this.state.mode}
                        onClick={task => console.log(task)}
                        onDateChange={(task, start, end) => console.log(task, start, end)}
                        onProgressChange={(task, progress) => console.log(task, progress)}
                        onTasksChange={tasks => console.log(tasks)}
                    />
                </div>
                ...

            )

        }

    }

## The API

### The component `props`

|      Property      | Description                                                                                         |
| :----------------: | :-------------------------------------------------------------------------------------------------- |
|      `tasks`       | Accepts array of class `Task`                                                                       |
|  `onTasksChange`   | Accepts a `(tasks: Task[]) => void`, where `tasks` is the new copy —manipulated— of array of tasks  |
|     `onClick`      | Accepts a `(task: Task) => void`, where `task` is the clicked task                                  |
|   `onDateChange`   | Accepts a `(task: Task, start: Moment, end: Moment) => void`, both start and end are Moment objects |
| `onProgressChange` | Accepts a `(task: Task, progress: number) => void`                                                  |
|   `onViewChange`   | Accepts a `(mode: ViewMode) => void`                                                                |
