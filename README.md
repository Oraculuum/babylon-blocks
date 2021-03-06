# babylon-blocks
Open Source Blockly library for Babylon.js

Getting started? Give Babylon Blocks a try [here](https://developers.oraculuum.com/babylonblocks/demo/index.html).

__Table of Contents__

* About
* Installing Babylon Blocks
* Contributing to Babylon Blocks
* Project History
* Adopt a Block List

## About

[Google Blockly](https://developers.google.com/blockly/) is an open source library for building visual programming editors and is used by the likes of [Code.org](https://code.org/) and [MIT App Inventor](http://appinventor.mit.edu/explore/).  [BabylonJS](http://www.babylonjs.com/) is a complete open source JavaScript library for building 3D games with HTML5, WebGL and Web Audio.  It is used by the likes of [Assassin's Creed Pirates](http://assassinscreed.ubi.com/en-us/games/assassins-creed-pirates.aspx) and others to deliver Graphics Processor Unit (GPU) accelerated 3D and 2D graphics in the browser on desktop, tablet, mobile, and even [virtual reality](http://www.slashgear.com/webgl-plants-game-in-oculus-rift-with-one-line-of-code-03323659/) devices without the need for plugins. 

Babylon Blocks is an open source project to combine these two awesome technologies by creating a library of Blockly blocks that interface with BabylonJS.  These so-called "babylon blocks" will not only make it possible to build 3D games and web applications visually, but will make learning 3D graphics programming fun and easy.

## Installing Babylon Blocks

Installing Babylon Blocks on your local machine so you can contribute or incorporate it into your own projects is easy.  

If you're an advanced user, create a new branch and check it out, commit your changes, and create a pull request to merge your changes with the master branch.  

If you're a less advanced user, just click "Download ZIP" in the upper right corner and unzip the files to a location of your choosing.  Then, when you're ready to submit your changes, you can use the "Branch: master" drop-down above to create a new branch and switch to it, use the edit icon above the file you wish to edit to add your changes, use the "Commit changes" button below the file you edited to commit your changes, and finally use the "New pull request" button above to submit your changes for review and approval.

Once you've downloaded the code, drag and drop the file "path-to-your-download/babylon-blocks/blockly/index.html" from a file folder into the URL bar of your web browser.  Boom.  You're up and running.  

## Contributing to Babylon Blocks

__There are two ways you can help__
* Build a babylon block using the instructions below (if everyone builds one block we can have this done in no time!).
* Donate $5 [here](https://developers.oraculuum.com/babylonblocks/demo/index.html) so we can pay someone to build a babylon block in your name.  The text "Dedicated to: your name here (or alter ego)" will be appended to the end of your block's tooltip... so that every time someone hovers over your block to learn more about it... they'll be forced to reflect on your greatness!

__Building a Babylon Block__  

Building a babylon block involves choosing a block to build, designing the block using the [Block Factory](https://blockly-demo.appspot.com/static/demos/blockfactory/index.html), defining a code generator for the block, adding the block to the blockly toolbox, and creating documentation for the block so others can use it.

1. Choose a babylon block to adopt from our "Adopt a Block List" at the bottom of this readme or add a babylon block of your choosing to the "Adopt a Block List" so everyone knows you're working on it.

   We'll build the [BABYLON.Mesh.CreateSphere(name, segments, diameter, scene, updatable)](http://www.sokrate.fr/documentation/babylonjs/BABYLON.Mesh.html) block as an example.

2. Design your block using the [Block Factory](https://blockly-demo.appspot.com/static/demos/blockfactory/index.html).  A video tutorial showing how to use the Block Factory can be found [here](https://www.youtube.com/watch?v=s2_xaEvcVI0).  Design your block using a similar naming convention, colour scheme, and layout as the create sphere block [here](https://blockly-demo.appspot.com/static/demos/blockfactory/index.html#zhutu3) so that your block fits in with the other babylon blocks and doesn't feel left out.  Also, avoid using punctuation in your block's wording, since punctuation does not translate well to other languages.

  Once your block is designed, copy and paste the __JSON__ definition of your block from the Block Factory's "Language Code: __JSON__" section into the block definition file "path-to-your-download/babylon-blocks/blockly/blocks/babylon.js" and wrap your __JSON__ definition in the following code:
  
  ```javascript
   Blockly.Blocks['your_blocks_name'] = {
      init: function() {
         this.jsonInit(
            // your block's JSON definition goes here 
         );
      }
   };
   ```
   
   The final block definition for our create sphere block will look like the following.  Don't forget to add a "helpUrl" (to the documentation you'll create in step 5) and a "tooltip" (feel free to put "Block created By: Your Name or Alter Ego"):
   
  ```javascript
   Blockly.Blocks['babylon_mesh_create_sphere'] = {
      init: function() {
         this.jsonInit(
            {
              "type": "babylon_mesh_create_sphere",
              "message0": "create Sphere with %1 name %2 %3 segments %4 diameter %5 scene %6 updatable %7 %8 side orientation %9",
              "args0": [
                {
                  "type": "input_dummy"
                },
                {
                  "type": "field_input",
                  "name": "NAME",
                  "text": "sphere1"
                },
                {
                  "type": "input_dummy"
                },
                {
                  "type": "input_value",
                  "name": "SEGMENTS",
                  "check": "Number"
                },
                {
                  "type": "input_value",
                  "name": "DIAMETER",
                  "check": "Number"
                },
                {
                  "type": "input_value",
                  "name": "SCENE",
                  "check": "BABYLON.Scene"
                },
                {
                  "type": "field_dropdown",
                  "name": "UPDATABLE",
                  "options": [
                    [
                      "false",
                      "false"
                    ],
                    [
                      "true",
                      "true"
                    ]
                  ]
                },
                {
                  "type": "input_dummy"
                },
                {
                  "type": "field_dropdown",
                  "name": "SIDE_ORIENTATION",
                  "options": [
                    [
                      "front",
                      "FRONTSIDE"
                    ],
                    [
                      "back",
                      "BACKSIDE"
                    ],
                    [
                      "double",
                      "DOUBLESIDE"
                    ]
                  ]
                }
              ],
              "inputsInline": true,
              "output": "BABYLON.Mesh",
              "colour": 212,
              "tooltip": "Create a new sphere. Block created by: nichol999",
              "helpUrl": "http://www.example.com/"
            }
         );
      }
   };
   ```
   
3. Define a code generator for the block.  The [Block Factory](https://blockly-demo.appspot.com/static/demos/blockfactory/index.html) generates a starter code generator for you.  Just copy and paste the __JavaScript__ generator stub for your block from the Block Factory's "Generator stub: __JavaScript__" section into the generator definition file "path-to-your-download/babylon-blocks/blockly/generators/javascript/babylon.js".

## Project History

Babylon Blocks was started as a side-project by Oraculuum's founder, John Nicholson, when he needed to teach a local Meetup group 3D graphics.  Since then it has matured into a full-fledged open source project supported by Oraculuum's Open Source Team, the Babylon Blocks community here on GitHub, and individual donors.

## Adopt a Block List

* ~~[BABYLON.Mesh.CreateSphere(name, segments, diameter, scene, updatable)](http://www.sokrate.fr/documentation/babylonjs/BABYLON.Mesh.html)~~ (adopted by: nichol999)
