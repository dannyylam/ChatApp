# ChatApp
A messaging application where users can send texts, images, and videos.
Utilized Firebase Authentication, Realtime Database, and Storage to make this application work.

Firebase Database Rules:
MUST be set to ".read": true, ".write": true

**Registration**<br>
This is the first screen users view once the app loads. Registration is required for new users. The required fields are Email and Password. Users can upload a profile pic also, which is done by clicking on the avatar icon just above the Login/Register segment.

We utilize Firebase for Authentication (Login and Registration). Profile images use a Storage service which Firebase provides as well.
    
**Login**<br>
By selecting the Login button from the segmented control, users are presented the Login form. A successful authentication directs users to their Active Messages screen.

Email and Password fields are Authenticated against ‘users’ stored in the Firebase database. Analytical data, specifically creation date and login dates are recorded in Firebase Authentication.

**Messages**<br>
User’s active messages are displayed here. In the navigation bar, the user’s name and profile image are displayed. A Create New Message button is displayed on the right side, (plus sign). Logout button is displayed on the left.
Messages are displayed through a UITableViewController.

We utilize a function to retrieve active and new messages within the “user-messages” child node by capturing the logged in user’s UID and then retrieving all messages associated with that UID as well as the “chatPartnerId” and the message content.

**Create New | Reply To Message**<br>
By tapping the Create New icon or selecting an active message from the messages screen, user can compose a message by tapping the ‘Enter message’ input field. The device keyboard displays once the input field is tapped.
Another feature includes the ability to send images or video by selecting the image icon displayed in the left in the input field.

In the View folder, the ChatInputContainer view controls UI for the message input field. The UserCell and ChatMessage views control the UI elements for the message content.

**Send Image/Video Message**<br>
By tapping the image icon from the message input controller, users can select an image or video available on their device. Once a media type is selected, the user is prompted to either cancel or choose - Tapping choose inputs the media into the message and the user can tap send to send the image or video

In the ChatLogController, we utilize an imagePicker method to enable selecting an image or video. We utilize Firebase Storage to store the media file. A url of its location in Firebase is captured and sent to the recipient user. 

**Firebase**<br>
The app utilizes three services provided by Firebase Authentication, Realtime Database, and Storage.

Our Realtime Database is organized by 3 groups: Users, Messages, and User-Messages.

The Users group contains values for all existing registered users, specifically name, email and profile image urls. These values are stored as child nodes to their respective unique user ids.
Messages are assigned unique ids and the contents are stored as child node values of the assigned unique id.
User-Messages are sorted by User and as child nodes to each user, a log of messages are stored
their for retrieval.

Authentication database is used for Signing in members and those records are stored there.

We use Storage to store images, video, and profile images. It is organized into those three groups respectively.
