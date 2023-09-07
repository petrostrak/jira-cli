## Jira CLI
A Jira clone for the terminal.

Two primary features in Jira will be implemented:

*  Epic CRUD
*  Story CRUD

![Alt Text](https://github.com/petrostrak/jira-cli/blob/main/jira-cli.gif)

## Manual Tests

Run these manual tests (___from top to bottom in order___) to see if your program works as expected.

__NOTE:__ Before running these tests, reset the database by updating `data/db.json` to this:
```json
{
    "last_item_id": 0,
    "epics": {},
    "stories": {}
}
```

__Create Epic__

Steps:
* `cd` into the root folder of the project
* Run `cargo run`
* Input `c` to create a new Epic
* Input `"New Epic name"` as Epic name
* Input `"New Epic description"` as Epic description
* Check if `db.json` matches with the following:
     ```json
    {"last_item_id":1,"epics":{"1":{"name":"New Epic name","description":"New Epic description","status":"Open","stories":[]}},"stories":{}}
     ```

__Create Story__

Steps:
* Input `1` to select the created Epic
* Input `c` to create a new Story in the selected Epic
* Input `"New Story name"` as Story name
* Input `"New Story description"` as Story description
* Check if `db.json` matches with the following:
    ```json
    {"last_item_id":2,"epics":{"1":{"name":"New Epic name","description":"New Epic description","status":"Open","stories":[2]}},"stories":{"2":{"name":"New Story name","description":"New Story description","status":"Open"}}}
    ```

__Update Epic__

Steps:
* Input `u` to update the selected Epic
* Input `2` to select `IN-PROGRESS` as the updated status
* Check if `db.json` matches with the following:
    ```json
    {"last_item_id":2,"epics":{"1":{"name":"New Epic name","description":"New Epic description","status":"InProgress","stories":[2]}},"stories":{"2":{"name":"New Story name","description":"New Story description","status":"Open"}}}
    ```

__Update Story__

Steps:
* Input `2` to select the created Story
* Input `u` to update the selected Story
* Input `3` to select `RESOLVED` as the updated status
* Check if `db.json` matches with the following:
    ```json
    {"last_item_id":2,"epics":{"1":{"name":"New Epic name","description":"New Epic description","status":"InProgress","stories":[2]}},"stories":{"2":{"name":"New Story name","description":"New Story description","status":"Resolved"}}}
    ```

__Remove Story__

Steps:
* Input `d` to delete the selected Story
* Input `Y` to confirm removal
* Check if `db.json` matches with the following:
    ```json
    {"last_item_id":2,"epics":{"1":{"name":"New Epic name","description":"New Epic description","status":"InProgress","stories":[]}},"stories":{}}
    ```

__Remove Epic__

Steps:
* Input `c` to create a new Story in the selected Epic
* Input `"New Story name"` as Story name
* Input `"New Story description"` as Story description
* Input `d` to delete the selected Epic
* Input `Y` to confirm removal
* Check if storage.json matches with the following:
    ```json
    {"last_item_id":3,"epics":{},"stories":{}}
    ```