# v4 Board Test Scripts

## Installation

To use the test scripts, you need to install sbot with:

```bash
pip install -r requirements.txt
```

## Usage

Each test board has its own test script.
Providing the `--log` argument along with a filename will log to CSV each board's test results.
Each test run is stored in a separate row in the CSV file.

### Power Board Test

This script expects the power board to have a >30A 12V power supply connected to the battery connector.
Each output port should be connected to a resistor of the value specified in the test script.

To test the low battery cut-off, you can use the `--test-uvlo` argument to enable the test.
This requires a 12V tenma power supply to be connected to the test computer over USB and a changeover circuit to be used to automatically switch between the high current power supply and the tenma power supply.

Run the test script with:

```bash
./power_test.py [--log <filename>] [--test-uvlo]
```

### Motor Board Test

This script expects the motor board to have a pair of 4.7 ohm resistors connected to the motor outputs, with 12V provided to the 12V port.

Run the test script with:

```bash
./motor_test.py [--log <filename>]
```

If you are using a power board that does not automatically turn on any 12V ports to provide power to the motor board, you can use the `--use-power-board` argument to enable port L2 before running the test.


### Servo Board Test

This script expects the servo board to have 12 servos connected to it, with 12V provided to the 12V port and 5V provided to the AUX port.

If you only want to test the first 8 servos then the 5V power supply is not required.

Run the test script with:

```bash
./servo_test.py [--log <filename>]
```

If you are using a power board that does not automatically turn on any 12V ports to provide power to the servo board, you can use the `--use-power-board` argument to enable port L2 before running the test.
