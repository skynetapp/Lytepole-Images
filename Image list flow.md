#### Date: 15/03/2017

#### Description: This document explains the code flow of Image list display.

#### Step 1:

Function **controlVideoListFlow** will be called first from index.php to controller which takes the inputs from the user. we call the wsdl to get the image list and displays.

- Function **createImageListInputVO** takes the inputs array and send to data file and prepares the list object.
- In action, function **createImageListInputVO** will be called from Data.php which gets the values from input array and sets the values for list value object to pass for WSDL call. It prepare the query and required input to create image.
- Input parameters will be meeting id,meeting name and Action name.
- Result returns the image list value object array to controller.

#### Step 2:

- Function **getRealationsList** is used to call the wsdl for getting the meeting related image.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **getRelationshipsListArray** in VideoWS.php which is used to send data to wsdl for getting the image and metting relation using the **get_relationships**.
- Creating parameters as session id, module name,module id,related module,order by,deleted.
- Result returns the relation id.

#### Step 3:

- If the count of relation id is greater than 1, then we will set the query and function **getImageList** will be called which is used to call the wsdl for getting the image.
- In action, first wsdl client connection will be set by function **setWSDLHandle**.
- Function **getListArray** is used to send data to wsdl for getting the image list array using the **get_entry_list**.
- Creating parameters for wsdl using objects.
- Result returns the image list array to controller.


#### Step 4:

- Function **createImageListDataObjectArr** creates a list object array for the data get from wsdl and passes to view page.
- In action, function **createImageListDataObject** will be called from VideoData.php gets the values from input array and sets the values for list data object to pass and to create image data.
- The parameters are name,id,date created,created by name,created by id,meeting name,meeting id,file ext.
- Result returns image data object array to controller.

#### Step 5:

- Function **showImageList** takes the input data object and gives to the image list .
- In action, function **showImageListView** will be called from ImageView.php which displays the tpl page.
- The image list tpl page will be **imageListForm.tpl** in views folder.

#### Step 6:

- If the relation id is empty, first we will set the Meeting Id and meeting name and function **showemptyImageList** will be called which takes the input data object and gives to the empty image view.
- From action, function **showemptyImageList** will be called to imageView.php which displays the tpl page.
- The tpl page will be **emptyimageListForm.tpl** in views folder.
