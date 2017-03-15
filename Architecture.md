#### Date: 15/03/2017

#### Description: This document explains the code flow of images.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Image
Views | imageListForm, emptyimageListForm


#### Architecture

- After login into lytepole, if we want to upload images we can go into messages and there we can upload the image for a member in chat.
- If the image is empty, form will be redirected to empty image list.
- Function **controlImageListFlow** will call the wsdl to get the image list and displays the output.
- Function **createImageFlow** will create a image and uploads the sugar folder using curl call.
