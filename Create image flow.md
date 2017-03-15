#### Date: 15/03/2017

#### Description: This document explains the code flow of creating image.

#### Step 1:

Function **createImageFlow** will be called first from index.php to controller which is used to create image, and uploads to sugar folder using curl.

- Function **createImageListInputVO** takes the inputs array and send to data file and prepares the list object.
- In action, function **createImageListInputVO** will be called from ImageData.php which gets the values from input array and sets the values for list value object to pass for WSDL call. It prepare the query and required input to create video.
- Input parameters will be meeting id,meeting name and Action name.
- Result returns the image list value object array to controller.

#### Step 2:

- Function **createImage** takes the input value object and passes to the wsdl call to create a image.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **createImage** will be called from ImageWS.php which is used to create a new image using wsdl calls **set_entry**. 
- Create the parameters for wsdl using object and passing parameter array to ws call.
- Result returns the image id to controller.

#### Step 3:

- Function **createMeetingImageRelation** takes the input value object and set relation between image and meeting.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **createMeetingImageRelation** in VideoWS.php which is used to create a relation between meeting and image using wsdl calls **set_relationship**.
- Creating parameters for wsdl using object and passing the parameter array to ws call.
- Result returns the relation id.
- Image will be saved using curl call.
