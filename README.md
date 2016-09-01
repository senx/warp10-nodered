Object msg: 
{ "_msgid": "f8f4fefe.070b", "topic": "", "payload": 1472737293700 }
pushed on stack

* Node WarpScript 

This module can be used to execute some WarpScript with node-red. This will be done by executing an HTTP POST to the Warp 10 url indicated in the warpscript node config.

** Input 

If an input is added before the warpscript node, then it pushes the message contained in it directly on the stack. If the message contains primitv types they are pushed as if on warpscript (String, Number and boolean), array are converted in List, object in Map, null in NULL, and Buffer in utf-8 string. 

A message on WarpScript have the following form:  

```
  { '_msgid' 'f8f4fefe.070b' 'topic' '' 'payload' 1472737293700 }
```

** WarpScript

Insert the WarpScript to execute on the input in the editor in the config of the warpscript node.

** Send message to output

In the config of the warpscript, it possible to enter as many output as possible in node-red. To send message to specific output let a map on the top of the stack. For example the following WarpScript code takes as input a message, store it in a variable then send two output message: one to the first output configured (transfered the message received), and then send a second output to another output with a new message containg a "test" payload.

'msg' STORE
{
    '0' $msg
    '2' { 'payload' 'test' }
}