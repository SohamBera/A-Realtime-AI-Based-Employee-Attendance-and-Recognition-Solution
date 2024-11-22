# A-Realtime-AI-Based-Employee-Attendance-and-Recognition-Solution
 a Realtime AI Based Employee Attendance and Recognition Solution
 We have to install v s code, Qt Desiner, SQLite and run in v s code.
 
PYQT5: Used for building the GUI (animation, events, and various widget classes).
sys: Provides access to system-specific parameters and functions.
sqlite3: Used for managing a local SQLite database where attendance records are stored.
datetime: Manages dates and times for attendance entries.
cv2: OpenCV library for image processing and facial recognition.
os: Manages directory structures and files.
numpy: Supports array handling needed for OpenCV image operations.
pygame: Manages sound playback for alerts.

initialize_mixer(): Initializes the mixer with specific settings for frequency and buffer size to ensure compatibility.
play_alert_sound(): Plays a sound file to alert the user of an unrecognized person.
stop_alert_sound(): Stops the sound playback.

MainApp: Inherits QMainWindow and ui (the UI file 'face-reco.ui').
self.setupUi(self): Sets up the UI elements from the .ui file (face-reco.ui).
Tab Navigation: Initializes the tab widget to show the first tab on startup and connects buttons to their respective methods.
Surveillance Banner: Creates a label banner with text, style, and animation to move it from right to left, indicating the surveillance status.
Digital Clock: Displays the current date and time using QLCDNumber. A QTimer updates the time every second.

initialize_mixer():Initializes the pygame mixer for sound playback.
stop_sound_button_pressed: Stops the sound and initializes the database by creating a table if it doesn't exist.
login/login2: Verifies the password and, if correct, switches the current tab to the main dashboard. If incorrect, it shows an error message.
update_time: Updates the digital clock displayed on the GUI with the current date and time.
logout: Logs the user out by switching to the login tab.
close_window: Closes the application.

handle_manual_attendance_entry: Allows the user to manually add or update attendance for a specific person by name.

load_reports: Populates the attendance report table from the SQLite database.
1.clean current entries
2.connects to the SQLite
3.to set the column count in the table widget
4.the setItem method is called to place the data in the corresponding cells of the report table
5.Set Column Headers and Formatting

show_selected_date_reports: Filters attendance records by date.
1.clean current entries
2.retrieves the selected date from the dateEdit widget
3.fetch records for the selected date.
4.The method inserts the retrieved data into the REPORTS table widget in the same way as in the load_reports method.
5.Set Column Headers and Formatting

start_training: Allows the user to add a new identity. It captures images from the webcam, detects faces using OpenCV, and stores them in a directory named after the person.
1.The method first checks if a folder exists for the new person in the datasets directory. If it doesn’t exist, it creates the folder.
2.It initializes the webcam and starts capturing images. The webcam feed is processed frame by frame.
3.After capturing the required number of images, it releases the webcam and closes the OpenCV window. Finally, it displays a success message to the user.

record_attendance: Captures webcam images, detects faces, and compares them with known faces. If the face is recognized, attendance is logged in the database with entry and exit times. If not, it triggers an alert sound and saves the image to an "unknown" folder.
1.The method loads the images from the datasets folder and prepares them for recognition. Each image corresponds to a person, and it assigns labels (IDs) to each person.
2.It then trains an LBPH (Local Binary Pattern Histogram) face recognizer using OpenCV. It uses the images and labels that were loaded in the previous step.
3.The webcam is opened, and for each frame, it detects faces using the CascadeClassifier. For each detected face, it tries to recognize it by comparing it with the trained model.

Recognition Scores Logging: Saves facial recognition scores to a text file for analysis.
main: Initializes the PyQt application and shows the main window.This code brings together GUI design, facial recognition, attendance recording, and audio alerts into a cohesive attendance management tool with PyQt and OpenCV.

