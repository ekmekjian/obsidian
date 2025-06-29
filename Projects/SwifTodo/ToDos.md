## Design (CLI Implementation)

### Models

- Task:
- Json Codable Tasks:

#### Task

- [X] Title
- [ ] DueDate
- [ ] Duration
- [ ] Priortiy 

### Views

- [X] ListView to create layout of the tasks:
- [ ] TaskView, layout view for a task:
  - [ ] Finish Task model properties ### Controllers

- [X] Accepts JSON into Task
- [X] Completing tasks:
  - [ ] When a task is compelted remove from the json

#### Due Date Controller

- [ ] keeps tracks of all Task.dueDate
- [ ] Interpret dueDate property JSON
- [ ] Time Date Validator:
	- [ ] When a task is saved a check must be made to see if date and time have any values
	- [ ] The date and time validator should see if either time or date is empty:
		- [ ] If date is empty but time isn't then return and error
		- [ ] if time is empty but date isn't then return date
- [ ] How do I check due date comming from json if there is a time or not?
	- check if it's in ISO8601 format?

#### Database Controller
**Current Issue:** When data is being imported all the tasks are coming with the same date and time.
- [ ] Create a database controller that will handle all the CRUD operations
#### File Manager:
- [X] check if the file and directory exists if not create it else load contents
- [X] Either gain permissions to write to .config or find new destination for JSON file

---

## Notes

There are 86400 seconds in a day
 Whether it's HStack or VStack each take an alignment paramter `(alignment:.center){`:

- .center(Center the elements)
- .leading(lean them towards the front)
- .trailing(lean them towards the end)
We can hide elements and reveal if conditions are met:

```swift
if counter > 1 {
    Button("Remove number") { counter -= 1 }
}
```
