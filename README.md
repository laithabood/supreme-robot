# supreme-robot
int; forward = 30; // Pin 12 - Forward
int; reverse = 40; // Pin 11 - Reverse
int; left = 51; // Pin 10 - Left
int; right = 39; // Pin 9 - Right

char; val; // Variable to receive data from the serial port

void; setup() {

// initialize the digital pins as output
pinMode(forward, OUTPUT);
pinMode(reverse, OUTPUT);
pinMode(left, OUTPUT);
pinMode(right, OUTPUT); Serial.begin(9600); // Start serial communication at 9600bps
}


// Fordward action
void; go_forward() {
digitalWrite(forward, HIGH);
digitalWrite(reverse, LOW);
}

// Reverse action
void; go_reverse() {
digitalWrite(reverse, HIGH);
digitalWrite(forward, LOW);
}


// Left action
void go_left() {
digitalWrite(left, HIGH);
digitalWrite(right, LOW);
}

// Right action
void go_right() {
digitalWrite(right, HIGH);
digitalWrite(left, LOW);
}

// Stop turn action
void stop_turn() {
digitalWrite(right, LOW);
digitalWrite(left, LOW);
}

// Stop car
void; stop_car() {
digitalWrite(forward, LOW);
digitalWrite(reverse, LOW);
digitalWrite(right, LOW);
digitalWrite(left, LOW);
}

// Read serial port and perform command
void; performCommand() {
if (Serial.available()) { val = Serial.read();
}; if (val == "w") { // Forward go_forward(); } else if (val == 's') { // Backward go_reverse(); } else if (val == 'd') { // Right go_right(); } else if (val == 'a') { // Left go_left(); } else if (val == 'l') { // Stop Turn stop_turn(); } else if (val == 'k') { // Stop stop_car(); }
}


void; loop() {
performCommand();
}
