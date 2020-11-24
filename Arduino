
  #include <Servo.h>
  // constants won't change. They're used here to set pin numbers:
  //const int buttonPin = 2;     // the number of the pushbutton pin
  const int ledPin =  3;      // the number of the LED pin

  // variables will change:
  int buttonState = 0;         // variable for reading the pushbutton status
  //int clicks = 0;
  Servo motor;
  int pos = 0;
  void setup() {
    motor.attach(7);
    pinMode(8, INPUT);
    //  clicks = 0;
    // initialize the LED pin as an output:
    pinMode(ledPin, OUTPUT);
    // initialize the pushbutton pin as an input:
    // pinMode(buttonPin, INPUT);
    //for python comm
    Serial.begin(9600); // use the same baud-rate as the python side

  }

  void loop() {
    // read the state of the pushbutton value:
    buttonState = digitalRead(8);
    if (Serial.available() > 0)
    {
      char data = Serial.read();
      if (data == 'C')
      {
        // if(buttonState == HIGH)
        if (buttonState == HIGH) {
          if (motor.read() != 90)
          {
            motor.write(30);
            delay(50);
            motor.write(60);
            delay(50);
            motor.write(90);
            delay(50);
          }

          digitalWrite(ledPin, HIGH);
        }
      }
      else if (data == 'V') {
        //delay(2000);
        if (motor.read() != -90)
        {
          motor.write(-30);
          delay(50);
          motor.write(-60);
          delay(50);
          motor.write(-90);
          delay(50);
        }
        digitalWrite(ledPin, LOW);
      }
    }
  }

  //PYTHON CODE THAT HAS TO DO WITH THIS

  // BEFORE WHILE LOOP:
  /*
    import serial <- Arduino and serial monitor library 
    ---
    bool Open = False <- indicates if gate 'should'
    be open or not;
    ---
    arduino = serial.Serial('COM9', 9600, timeout=.1)
      {Initializes connection with Arduino board,
      'COM9' is the USB PORT, that the board is connected to.
      Change, if applied to another PC 
      (look in device manager to learn what port is used)}  
    time.sleep(1) <- Gives a second for stuff to load up 
       ' safety precaution ;) '
    ---
    msg = 'C' - char variable, indicates if mask is detected
    clr = 'V' - char variable, indicates if reqs arent met
  */
  //INSIDE WHILE LOOP:
  /*
     if keyboard.is_pressed('g'):
          ser.close()	
          cv2.destroyAllWindows()
          vs.stop()		
          sys.exit
      CLICK 'g' BEFORE EVERY SHUT DOWN OF THE PROGRAM,
      OTHERWISE FURTHER OPERATION IS SUSCEPTIBLE TO FAULTS!

       IF CASE OF ERRORS:
              ~~~    
      1.CLOSE THE .py SCRIPT
      2.UNPLUG THE BOARD
      3.RESTART THE COMPUTER
      4.PLUG THE ARDUINO BACK IN
      5.RUN THE SCRIPT AGAIN
                      - 
      problem should be fixed if steps are followed in 
      correct order :) 
                      -
              ~~~
      ---
      Open = True <- Opens the gates on start up, and keeps
          them open if face masks are detected
      ---
      if frame is not None:
          frame = imutils.resize(frame, width=400)	
      else:   <--- if condition is met, nothing happens,
                   ELSE if the camera malfunctions, gates 
                   close automatically
          arduino.write(clr.encode())
          print('GATE IS CLOSED')
          continue
      ---
      THESE CHECKS PERFORM AFTER FACE DETECTION PHASE:
      if Open:
          arduino.write(msg.encode())	<- this command writes 'C'
                                         in the serial monitor, 
                                         which opens the gate
          print('GATE IS OPEN')
      else: 
          arduino.write(clr.encode()) <- this command writes 'V'
                                          in the serial monitor,
                                          which closes the gate
          print('GATE IS CLOSED')
  */

