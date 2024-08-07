<h1>Key Word Spotting on Arduino Nano 33 BLE</h1>

<b>In this project I will demonistrate the steps, for ML workflow, KWS application arcitecture and deployment. ML workflow loops through collecting a data and making inferences, with more steps in between as shown below. It incorporates, loss functions, data augumentation, gradient descent, regression, classification, quantization, optimization, pruning, filters, neural networks, pre-processing, inferences, and post-processing steps.</b>

<img width="620" alt="image" src="https://github.com/user-attachments/assets/6f732903-70e6-4ff0-a8bf-e3275b35222a">


<b>Key word Spotting application architecture has 4 distinct steps, Initialization, pre-processing, inference, and post-processing.</b>
- Initialization has sub-steps, first we have to declare the variables, then load the data with "g-model" function, choose resolve operators, initialize interpreter, allocate arena for memory, define model inputs, then we will set up the main loop.
- Pre-processing is part of the main loop, performed before inference. It involves Audio provider and feature extractor.
- Inference is also part of the main loop comes next to the pre-processing where we prepare input tensors and invoke interpreters. we just have to make sure the input buffers are set up properly.
- post-processing is done to make sure that we have confidence in our results. Command recognizer and command responder is used for this step.
<img width="464" alt="image" src="https://github.com/user-attachments/assets/8cf273c5-bdda-475a-904f-feff69b87ed1">

<h2>Deploying the Pretrained KWS Model</h2>
<b> With the above steps I could be able to pretrain my model, now I will deploy it to my Arduino nano 33 BLE microcontroller via Arduino IDE.</b>

<h2>Load the pretrained Tensorflow Lite model</h2>

<img width="677" alt="image" src="https://github.com/user-attachments/assets/320c0010-e6d8-4f85-9efb-657e40e411dc">

<h2>Generate a TensorFlow Lite for Microcontrollers Model</h2>
<b>To convert the TensorFlow Lite quantized model into a C source file that can be loaded by TensorFlow Lite for Microcontrollers on Arduino we simply need to use the xxd tool to convert the .tflite file into a .cc file.</b>
<img width="649" alt="image" src="https://github.com/user-attachments/assets/77b4de85-0992-4c2f-97f4-577bd69a16d0">
<img width="623" alt="image" src="https://github.com/user-attachments/assets/6a5b0450-3bba-47fd-aa83-1b8be00dc401">
<img width="501" alt="image" src="https://github.com/user-attachments/assets/bb198b0c-de69-42ea-a3a8-f9b2afb85381">

<b>Next I'll Use a USB cable to connect the Arduino Nano 33 BLE Sense to my machine. I should see the green LED power indicator come on when the board first receives power.</b>
- I will first Select the Arduino Nano 33 BLE as the board by going to Tools → Board: <Current Board Name> → Arduino Mbed OS Boards (nRF52840) → Arduino Nano 33 BLE.
- Then, I'll select the USB Port associated with my board. This will appear differently on Windows, macOS, Linux, but will likely indicate ‘Arduino Nano 33 BLE” in parenthesis. I'll select this by going to Tools → Port: "COM3" → COM3(Arduino Nano 33 BLE).
- Use the rightward arrow next to the ‘upload’ / flash the code. I know now the upload is complete when I see red text in the console at the bottom of the IDE that shows 100% upload of the code.
- I should now have a working Keyword Spotting model for “Yes” and “No” deployed to my Arduino! To test it out, I'll open the Serial Monitor. I should start to see the result of the model “Yes, No, Unknown, Silence” begin to display in the Serial Monitor.

<img width="389" alt="image" src="https://github.com/user-attachments/assets/a1a41961-d495-4a3a-a657-e1802e7ea111">

<b>This should match the multicolor LED near the Bluetooth module on the board changing colors as follows:</b>

- Yes = Green LED
- No = Red LED
- Unknown = Blue LED
- Silence = Nothing
<img width="359" alt="image" src="https://github.com/user-attachments/assets/18f02769-92d3-4238-8b92-5d987fa3b11d">
<img width="323" alt="image" src="https://github.com/user-attachments/assets/d3295066-56c6-46a4-ab85-2dad3b0d465a">









