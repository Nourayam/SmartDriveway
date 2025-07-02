# Smart Driveway System - User Guide

## System Overview

The Smart Driveway System is an integrated home automation solution that provides:

1. **Vehicle Location Tracking**: Monitors your vehicle's proximity to your home
2. **Temperature Monitoring**: Tracks driveway temperature and controls heating
3. **Light Control**: Manages driveway lighting based on conditions
4. **Security Features**: License plate recognition and motion detection

All components work together to provide a seamless user experience.

## Getting Started

### System Requirements

- Python 3.7 or higher
- Tkinter (included with Python)
- Paho-MQTT: `pip install paho-mqtt`
- SpeechRecognition (for voice control): `pip install SpeechRecognition`

### Running the System

1. Start the MQTT broker on your local machine:
   - If using Mosquitto: `mosquitto -v`
   - Or set the broker to "broker.hivemq.com" in settings for a public broker

2. Run the main application:
   ```
   python smart_driveway_main.py
   ```

3. The dashboard will appear, showing all system components.

## Dashboard Overview

The dashboard is divided into two main sections:

### Status & Controls (Left Panel)

- **System Status**: Shows the current state of all components
  - Temperature and heating status
  - Light status
  - Vehicle location and detected license plate
  - Garage door status
  - Security system status

- **Manual Controls**: Allows direct control of system components
  - Heating ON/OFF
  - Light ON/DIM/OFF
  - Garage Door OPEN/CLOSE
  - Security ARM/HOME/DISARM

- **Vehicle Location Visualisation**: Shows your vehicle's position relative to your home

### Notifications & Camera (Right Panel)

- **Camera Feed**: Shows the simulated camera view with license plate recognition
- **Notifications**: Displays system alerts and status messages

## Settings

Access settings by clicking the "Settings" tab:

- **MQTT Settings**: Configure the broker connection
- **Notification Settings**: Enable/disable notifications
- **Voice Control Settings**: Enable/disable voice recognition
- **Temperature Thresholds**: Set heating activation thresholds
- **System Control**: Restart or stop the system

## Features

### Temperature Control

- Automatically activates heating if temperature falls below threshold (default 18°C)
- Automatically deactivates heating if temperature rises above threshold (default 24°C)
- Sends notifications for extreme temperatures (below 0°C or above 30°C)
- Manual control available through the dashboard

### Light Control

- Automatically turns on lights when garage door opens
- Dims lights at night (8PM-6AM) to save energy
- Brightens to full when motion is detected, returns to dim after 10 minutes
- Adjusts brightness based on temperature
- Manual control available through the dashboard

### Vehicle Location

- Tracks vehicle distance from your home
- Automatically opens garage door when owner's vehicle approaches (if enabled)
- Activates lights and adjusts security system when vehicle is near
- Provides notifications about parking availability and safety

### Camera & Security

- Recognises license plates of approaching vehicles
- Distinguishes between owner and unknown vehicles
- Detects different types of motion (people, vehicles, etc.)
- Sends notifications for security events
- Activates appropriate responses based on detected events

### Voice Control

The system is supposed to be able to respond to various voice commands, including:

- "What's the temperature?"
- "Turn heating on/off"
- "Turn lights on/off/dim"
- "Open/close garage door"
- "Enable/disable notifications"
- "System status report"

Simply speak clearly after enabling voice control in settings. (with further development this will be fulfilled)

## Troubleshooting

### MQTT Connection Issues

If the system can't connect to the MQTT broker:

1. Check that the broker is running
2. Verify the broker address and port in Settings
3. Ensure no firewall is blocking the connection
4. Try using a public broker like "broker.hivemq.com"


### General Issues

If the system isn't responding correctly:

1. Check the notification panel for error messages
2. Restart the system using the button in Settings
3. If problems persist, restart the application

## Customisation

The system can be customised by modifying the constants at the top of the source code:

- `MQTT_CONFIG`: Change the broker settings
- `TOPICS`: Modify the MQTT topic structure
- Temperature thresholds, proximity thresholds, etc.

## Future Enhancements

Planned future enhancements include:

- Mobile app integration
- Weather API integration
- Additional sensors support
- Extended voice command vocabulary
- Machine learning for better vehicle and person recognition
- An actual working voice control (it was partially implemented but one of the packages didn't work)

## Support

For additional support, please contact your system administrator or refer to the technical documentation.
