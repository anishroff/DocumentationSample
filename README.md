# Sample Documentation




## sendActivationCode


POST URL: api/SampleApp/sendActivationCode/format/json


parameters:

	fullname : String  
	phoneno : String  


Response:

	{}
	
	
## resendActivationCode


POST URL: api/SampleApp/resendActivationCode/format/json


parameters:

	phoneno : String  


Response:

	{}



## SignIn


POST URL: api/SampleApp/signin/format/json


parameters:

	username in form of phoneno :  String *required
	activation_code: String *required
	latitude : String
	longitude : String
	
Response:

	{accessToken: String , username: String}


## SignOut


POST URL: api/SampleApp/signout/format/json


parameters:

	accessToken :  String *required

	
Response:

	{ success: "Signed out."}

	

## getUserDetails


POST URL: api/SampleApp/getUserDetails/format/json


parameters:

	accessToken :  String *required

	
Response:

	{ username: String, fullname: String, phoneno: String, picture: String, email: String, location : String }
	
	
## updateProfile


POST URL: api/SampleApp/updateProfile/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	fullname : String
	dob : date format yyyy-mm-dd
	notificationFlag : 0|1
	syncFlag : 0|1
	accountPlan : Free|Premium
	picture : file format jpg|jpeg|png
	email : String
	location : String

	
Response:

	{success: "Profile updated successfully."}
	
	
## createFolder


POST URL: api/SampleApp/createFolder/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	foldername : String
	parentFolderID: Integer
	
Response:

	{success: "Folder has been created.", folderID: Integer, folderName: String}	
	
	
## deleteFolder


POST URL: api/SampleApp/deleteFolder/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	folderID : Integer

Response:

	{success: "Folder has been deleted." , folderID: Integer}	
	
	
## renameFolder


POST URL: api/SampleApp/renameFolder/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	folderID : Integer
	folderName : String

Response:

	{ success: "Folder has been renamed.", folderName: String, folderID: Integer }	
	
	
## moveFolder


POST URL: api/SampleApp/moveFolder/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	folderID : Integer
	parentFolderID : Integer

Response:

	{success: "Folder has been moved.", folderID: Integer}	
	
	
## uploadFile


POST URL: api/SampleApp/uploadFile/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	file : file
	folderID : Integer
	mediaType : string audio|notes|photo|pdf

Response:

	{success: "File has been uploaded.", fileID: Integer, fileName: String, folderID: Integer}	
	
	
## deleteFile


POST URL: api/SampleApp/deleteFile/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	fileID : Integer
	
Response:

	{success: "File has been deleted.", fileID: Integer}	
	
	
## renameFile


POST URL: api/SampleApp/renameFile/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	fileID : Integer
	fileName : String
	
Response:

	{ success: "File has been renamed.", fileName: String, fileID: Integer}	
	
	
## moveFile


POST URL: api/SampleApp/moveFile/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	fileID : Integer
	folderID : Integer|0 for root folder
	
Response:

	{success: "File has been moved.", fileID: Integer}	


## fileIO


POST URL: api/SampleApp/fileIO/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	operation : string (copy|move|delete)
	files : json encoded array of (id, type)
	targetFolderID : integer | null
	
Response:

	{}


	
	
## getFolderDetail


POST URL: api/SampleApp/getFolderDetail/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	folderID : Integer|0 for root folder
	
Response:

	
	[{id : Integer,name : String, type: folder, path : String, server_path : String}, { id : Integer, name:String ,type:photo|note|pdf|audio, path : String, server_path : String}]



## getFileDetail


POST URL: api/SampleApp/getFileDetail/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	mediaID : Integer|0 for root folder
	
Response:

	{
		media_id: Integer
		media_name: String
		media_folder_id: Integer
		media_type: photo|pdf|note|audio
		media_server_path: String (Amazon server path)
		media_local_path: String (Mobile app local path)
		
		comments: [1]
		{
			userID: Integer
			name: String
			picture: String
			date: Date & Time
			comment: String
			filename: String
		}
		
		favorites: [1]
		{
			userID: Integer
			name: String
			picture: String (Amazon file path)
		}
	}	
	
	
## markFavorite


POST URL: api/SampleApp/markFavorite/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	itemID : Integer
	type : string (media|folder)
	
Response:

	{"success":"Marked as favorite.", "mediaID":"Integer"}
	

## unmarkFavorite


POST URL: api/SampleApp/unmarkFavorite/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	itemID : Integer
	type : string (media|folder)

	
Response:

	{ success: "Unmarked as favorite.", mediaID: "Integer"}	

	
## addComment


POST URL: api/SampleApp/addComment/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	mediaID : Integer
	commentText : String
	commentFile : file
	
Response:

	{success: "Comment has been added.", mediaID: Integer }	
	
	
## addFeedback


POST URL: api/SampleApp/addFeedback/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	feedbackSubject :: string
	feedbackText :: string
	
Response:

	{}
	

## inviteFriends


POST URL: api/SampleApp/inviteFriends/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	numbers : searlized array
	
Response:

	{}
	
## shareFiles


POST URL: api/SampleApp/shareFiles/format/json


parameters:

	username as phoneno :  String 
	accessToken : String
	share_id : integer
	type : file | folder
	mobileNo : Array of json encoded mobile number
	
Response:

	{}
	

## getFAQ


POST URL: api/SampleApp/getFAQ/format/json


parameters:

	
Response:

	{URL of FQA html}
