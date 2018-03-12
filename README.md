#Nebula frontend challenge

You need to simulate the procedure of a task life cycle, <i><u>Note: don't worry about the code execution</u></i>.

First, some simple background of blockchain interface :

    {
        "constant": false,
        "inputs": [
            {
                "name": "_app_id",
                "type": "uint256"
            },
            {
                "name": "_name",
                "type": "string"
            },
            {
                "name": "_data",
                "type": "string"
            },
            {
                "name": "_script",
                "type": "string"
            },
            {
                "name": "_output",
                "type": "string"
            },
            {
                "name": "_params",
                "type": "string"
            }
        ],
        "name": "create_task",
        "outputs": [
            {
                "name": "",
                "type": "address"
            }
        ],
        "payable": true,
        "stateMutability": "payable",
        "type": "function"
    }

In the above example and the json file found in the abi folder, it's a json representation of a solidity contract function interface. In other word, it's the interface for any outside code to communicate with blockchain.

the keys of this json objects that matters are : <i>inputs, outputs and names</i>. The others are not that important for this test.

This json object written as a js function would be:

    function create_task(_app_id, _name, _data, _script, _output, _param, callback){
        //do something ...
        let address = "some address that is twenty charactors in length";
        callback(error, address);
    }

Note the callback in the function parameter, it is automatically included when the json is parsed to interface. It <i>must</i> be included for it to work properly and get any response from blockchain.

Write a js script that perform the following tasks:

Client: 
- creates a task
- wait for task start indication 
- wait for task completion indication, there are three possible outcome of a task
    - completed 
    - error (a reported error state, not code execution error of js or blockchain)
    - cancelled 
    - These status are simply reported by the get_status method, if the returning value is not 0, meaning something has happened
- while waiting for these signals your code needs to be able to handle these situations accordingly
    - i.e. after a task is reported as started, three different outputs are possible, handle it accordingly
- hint, use promise to achieve these functions
- use setTimeout(callback,time) to check for status change
- using AngularJs or react would be a plus.
- bonus: handle page reload situation where you need to resume to proper waiting status

Again, don't worry too much about code execution, make it as clear as possible would be enough. 

