# Smart-Breathalyzer
 A transformative Smart Breathalyzer system designed to redefine responsible drinking practices and enhance road safety. Utilizing an MQ3 alcohol sensor, the system accurately finds intoxication levels in individuals. Upon detecting intoxication, an integrated camera captures the vehicle's number plate (tesseract), sends it to a centralized Google Sheets (via Google Cloud Console) triggering a comprehensive database search (Atlas – MongoDB) for the driver's details, including name, phone number, and license number. <br />
![image](https://github.com/mvipinchand/IntelliGuard-Breathalyzer-A-Smart-Intoxicant-Detection-System/assets/73341926/060e95ce-1e82-4a13-90e7-fe479c50099c) <br />
This information is then used to penalize the intoxicated individual for potential drink and drive offenses. The system automates the penalty process and issues notifications via email (Simple Mail Transfer Protocol - SMTP) to the offender, ensuring effective intervention. Our project encompasses the development, integration, and evaluation of this innovative system, presenting a novel approach to discourage drunk driving and promote a safer community. <br />
The captured frame is converted to grayscale and then subjected to bilateral filtering and edge detection (Canny) to enhance the license plate's visibility. Contours are detected in the processed image, and the largest contour, assumed to be the license plate, is identified. In order to identify the outline of the image, namely to detect the edge of the image, the relevant differential operator will be used.[3] The script then creates a mask based on the detected contour and applies it to the original image to isolate the license plate. The isolated license plate region is then cropped and saved as a separate image.
Tesseract OCR is applied to the cropped license plate image to extract the alphanumeric characters. Tesseract is available for Linux, Windows and Mac OS X, however, due to limited resources only Windows and Ubuntu are rigorously tested by developers.<br />
![License_Detection](https://github.com/mvipinchand/IntelliGuard-Breathalyzer-A-Smart-Intoxicant-Detection-System/assets/73341926/8f288da9-90b5-48d3-aa63-e2f71e6f0a76)<br />
The DHT11 sensor is interfaced with the Raspberry Pi to monitor temperature and humidity levels. Physically connecting the sensor involves wiring its data pin to a GPIO pin on the Raspberry Pi. For communication, the sensor employs a singlewire digital protocol. The Python script reads data from the sensor using the `Adafruit_DHT` library, which simplifies communication with DHT sensors on the Raspberry Pi. The library allows the Raspberry Pi to send a signal to the sensor, receive the sensor's response, and interpret the digital signal to obtain temperature and humidity readings. The acquired data is then processed for display on the LCD module and transmitted to Ubidots for remote monitoring and analysis. The Raspberry Pi communicates with Ubidots, an IoT platform, to securely transmit the temperature and humidity data. Ubidots employs the HTTP protocol for data exchange. The Python script utilizes the `requests` library to send an HTTP POST request to the Ubidots API, including the temperature and humidity values. Ubidots processes this data and updates a predefined dashboard. In Ubidots, a dashboard is configured to visually represent the real-time data received from the Raspberry Pi. Users can access this dashboard through the Ubidots web interface, providing a comprehensive view of temperature and humidity trends over time. This integration allows for efficient remote monitoring and analysis, enabling users to make informed decisions based on the environmental conditions captured by the DHT11 sensor connected to the Raspberry Pi.<br />
![image](https://github.com/mvipinchand/IntelliGuard-Breathalyzer-A-Smart-Intoxicant-Detection-System/assets/73341926/aa8818d9-391b-4c71-b750-dbbc65d9634b)<br />
Upon detecting an intoxicated driver, the system initiates a series of actions to notify the driver and relevant authorities. Once the license plate information is successfully extracted using image processing techniques, the system queries a MongoDB database to retrieve personal details of the driver. This information includes the driver's name, mobile number, and email address. Subsequently, these details are displayed on the LCD display, providing immediate feedback to law enforcement personnel or any on-site authorities. Simultaneously, a comprehensive email notification is prepared, addressing the driver directly. The email content notifies the driver of the penalization, indicating the vehicle's license plate number, the specific charge, and the prescribed penalty amount. This personalized communication aims to raise awareness and ensure that the driver is promptly informed of the consequences of driving under the influence. The email notification is sent using the Simple Mail Transfer Protocol (SMTP), with the Python `smtplib` library facilitating the communication between the Raspberry Pi and the email server. The system configures the email subject, body, and recipient based on the extracted details from the MongoDB database. Additionally, an image attachment of the cropped license plate region serves as a visual record of the incident. This attachment enhances the communication by providing concrete evidence of the detected violation. The use of email notifications not only informs the driver but also serves as a formal communication channel, ensuring accountability and compliance with legal procedures. It reinforces the severity of the offense and emphasizes the need for responsible driving behaviour. Incorporating multifaceted notifications, including LCD display updates and personalized email communication, contributes to an efficient and comprehensive smart breathalyzer system. Displaying driver details on the LCD screen in real-time enhances on-site decisionmaking for law enforcement, while the email notification adds a layer of accountability and awareness for the driver. By leveraging the capabilities of both local display and remote communication, the system maximizes its impact in addressing the critical issue of drunk driving. This holistic approach aims not only to enforce penalties but also to educate and promote responsible driving behaviour for improved road safety.
