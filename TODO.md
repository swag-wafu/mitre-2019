# Description

TODO: Remember where I put that flag…

http://138.247.13.110/

# Solution

Using the debugger of Firefox, I find the script `lists.js`. Inside, there is some javascript code. A line is particularly interesting: `var todoURL = '/api/todos/' + todoID + '/'`.

Why not check `http://138.247.13.110/api/todos/`? We found the complete list of todo list! We can find easily the flag in there: 
```
    {
        "id": 678,
        "todolist": 678,
        "description": "MCA{al3x4_5et_a_r3minder}",
        "created_at": "2019-02-23T17:22:16.462620Z",
        "is_finished": false,
        "finished_at": null
    }
```
