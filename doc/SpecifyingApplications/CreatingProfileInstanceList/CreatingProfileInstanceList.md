# Creating a ProfileInstanceList

This is a step by step cookbook for creating the _ProfileInstanceList_.  

**Please, read the background information about the [Concept of _Profiles_](../../ElementsApplicationPattern/Functions/ConceptOfProfiles/ConceptOfProfiles.md) and the [Concept of the _ProfileInstanceList_](../ConceptOfProfileList/ConceptOfProfileList.md) before working at the _ProfileList_.**   


### File Handling  

* Assure that there is a copy of the latest [template of the _ProfileInstanceList_](https://github.com/openBackhaul/ApplicationPattern/blob/develop/spec/ApplicationPattern%2BprofileInstances.yaml) in the _develop_ branch of your application's repository. The latest _ApplicationPattern+profileInstances.yaml_ can be downloaded from the [_ApplicationPattern_ repository](https://github.com/openBackhaul/ApplicationPattern/tree/develop).  
* Rename the file, by replacing "ApplicationPattern" by your application's name.  


### Preparation  

* If not yet existing, create an _Issue_ for elaborating the _ProfileInstanceList_.  
* Open a local feature branch for elaborating the _ProfileInstanceList_.  


### General  

* Re-using already existing descriptions of instances of _Profiles_ from _ProfileInstanceLists_ of other applications is very much recommended.  


### Further Instances of ActionProfile  

* Check your _ServiceList_ for services that are implementing the concept of _GenericRepresentation_.  
* If you would need to add further instances of _ActionProfile_ please look into existing applications' _ProfileInstanceLists_ and the template to get familiar with the concept.  
* Copy/paste and alter additional instances of _ActionProfile_ for configuring a step-by-step-clicking-through-process after starting with _/v1/start-application-in-generic-representation_.  
* Finally, just delete the form that waits for completion.  

**ProfileName**  
* The _ProfileName_ shall be set on "ActionProfile".  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* The _LayerID_ shall be set on "action".  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same _LayerID_.  

**OperationName**  
* Fill in the name of the operation (e.g. _/v1/start-application-in-generic-representation_) that shall transport the information about labels, input values and consequent requests in its response body to the _GenericRepresentation_.  

**Label**  
* Fill in the text (e.g. 'Inform about Application') that shall be printed on a button, which shall be represented in the _GenericRepresentation._  

**InputValueList::FieldName**
* If the request needs to send parameters in its body, these parameters have to be defined in the _InputValueList_.  
* Don't represent the _InputValueList_, if not required.  
* Be aware that the _FieldName_ will not just be sent as an attribute's name in the body of the request, but also be represented by the _GenericRepresentation_ besides an input field.  
* Fill in the _FieldName_ in UpperCamelCase notation.  

**InputValueList::Unit**
* The _Unit_ will be represented by the _GenericRepresentation_ besides an input field.  
* Don't represent this stereotype, if not required.  

**DisplayInNewBrowserWindow**  
* Usually, _DisplayInNewBrowserWindow_ is set on false and the response to the described request will be presented in the same browser window.  
* If the response to clicking the button shall be represented in a new window of the _GenericRepresentation_, _DisplayInNewBrowserWindow_ has to be set on true.  

**ConsequentOperationReference**  
* Operation that shall be called, whenever the button gets pressed in the _GenericRepresentation_.
* Because several parts (e.g. IP address, TCP port, _OperationName_) of the URL that has to be called by the _GenericRepresentation_ might be subject to configuration in your application, there shall be just a reference to the operation here. The actual URL will then be generated by your application right before responding on a request reaching the _OperationName_.  
* UUIDs comprised in the references have to match the _ServiceList_ content (otherwise the application will fill wrong data into the response bodies of the _GenericRepresentationRequests_ during run-time).  


### Instances of FileProfile  

* Whenever your application is supposed to use one or several files for storing data, a corresponding number of instances of _FileProfile_ is required.  
* Just copy/paste the form prepared for completion or copy from existing _ProfileInstanceLists_ of other applications.  
* Finally, just delete the form that waits for completion.  

**ProfileName**  
* The _ProfileName_ shall be set on "FileProfile".  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* The _LayerID_ shall be set on "file".  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same _LayerID_.  

**FileIdentifier**  
* Document an invariant identifier of the file.  
* If the application uses just one file for storing its data, 'applicationData' might be a good choice.  

**FileDescription**  
* Document the content of the file.  
* Even if the exact format of the information is to be defined by the implementer, the information could be listed here.  

**file-path**  
* The content of this field is actually determined by the implementer.  
* Maybe, '../application-data/application-data.json' is a good choice for being a default value.  

**UserName**  
* This field is not mandatory.  
* If access to the file shall be protected by user name and password, some value should be added here.  
* Maybe, the application's name is a good choice.  

**Password**  
* This field is not mandatory.  
* If access to the file shall be protected by user name and password, some value should be added here.  

**Operations**  
* This field allows restricting the access rights of the application to the file.
* Values are to be chosen from 'read', 'write' or 'off'.
* In case of updating an existing application, it is recommended to configure 'off' for supporting harmfree handover of the already existing data file during the embedding process.


### Further Instances of GenericResponseProfile  

* Check your _ServiceList_ for services that are implementing the concept of _GenericRepresentation_.  
* If you would need to add further instances of _GenericResponseProfile_ please look into existing applications' _ProfileInstanceLists_ and the template to get familiar with the concept.  
* Copy/paste and alter additional instances of _GenericResponseProfile_ for configuring the responses given by the _GenericRepresentationRequests_.  
* Finally, just delete the form that waits for completion.  

**ProfileName**  
* The _ProfileName_ shall be set on "GenericResponseProfile".  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* The _LayerID_ shall be set on "response".  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same _LayerID_.  

**OperationName**  
* Fill in the path of the request that shall contain provide the response.  

**StaticFieldName**  
* The response will be represented in a field. This field will have a name/title. If this field name would be static, you could state it here.  

**FieldNameReference**  
* The response will be represented in a field. This field will have a name/title. If this field name would be stored somewhere in the internal data tree, you could reference this possition here.  

**Description**  
* This attribute is just for documenting the meaning of the defined field.  
* It is explanatory only and will not be passed to the _GenericRepresentation_.  

**Datatype**  
* Fill in the datatype of the response value.  
* Chose from 'string', 'integer', 'boolean'.  

**StaticValue**  
* The response will represent a value. If this value would be static, you could state it here.  
* The value has to be transported as a string, but might be interpreted according to the _Datatype_ at the receiving side.  

**ValueReference**  
* The response will represent a value. If this value would be stored somewhere in the internal data tree, you could reference this possition here.  
* The value has to be transported as a string, but might be interpreted according to the _Datatype_ at the receiving side.  


### Instances of IntegerProfile  

* Whenever you would like to make an aspect of the application's behavior configurable and this aspect can be expressed as an Integer value, an additional instance of _IntegerProfile_ is required.  
* Just copy/paste the form prepared for completion or copy from existing _ProfileInstanceLists_ of other applications.  
* Finally, just delete the form that waits for completion.  

**ProfileName**  
* The _ProfileName_ shall be set on "IntegerProfile".  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* The _LayerID_ shall be set on "integer".  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same _LayerID_.  

**IntegerName**  
* Document the attribute's name.  

**Unit**  
* Document the attribute's unit.  
* Don't represent this stereotype, if not required.  

**Minimum**  
* Fill in the minimum value that shall be accepted, while configuring the attribute via the individual OaM section of the REST API.  
* Don't represent this stereotype, if not required.  

**Maximum**  
* Fill in the maximum value that shall be accepted, while configuring the attribute via the individual OaM section of the REST API.  
* Don't represent this stereotype, if not required.  

**IntegerValue**  
* Fill in the current value, respectively the value that shall be applied right after instantiating the application.  


### Instances of StringProfile  

* Whenever you would like to make an aspect of the application's behavior configurable and this aspect needs to be expressed as a String, an additional instance of _StringProfile_ is required.  
* Just copy/paste the form prepared for completion or copy from existing _ProfileInstanceLists_ of other applications.  
* Finally, just delete the form that waits for completion.  

**ProfileName**  
* The _ProfileName_ shall be set on "StringProfile".  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* The _LayerID_ shall be set on "string".  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same _LayerID_.  

**StringName**  
* Document the attribute's name.  

**Enumeration**  
* If only a predefined set of values (e.g. operation modes) shall be accepted, while configuring the attribute via the individual OaM section of the REST API, put a comma separated list of these values into cornered brackets here.  
* Don't represent this stereotype, if not required.  

**Pattern**  
* If only strings that are following a generic definition shall be accepted, while configuring the attribute via the individual OaM section of the REST API, a Regex expression can be defined as a pattern.  
* Formulating Regex is not easy. Potentially [this documentation](https://user.phil.hhu.de/~seyffarth/classes/python2020/09-01%20Regular%20Expressions%20schreiben.html) might be helpful.  
* [Test the Regex](https://regex101.com/).  
* Don't represent this stereotype, if not required.  

**StringValue**  
* Fill in the current value, respectively the value that shall be applied right after instantiating the application.  


### New Profiles  

* You are free to instantiate as many objects based on the self-defined _Profiles_ as you like.  
* Just copy/paste the lines for _ProfileName_ and UUID from an existing definition and the additional stereotypes of your attribute or composed datatype.  
* Be aware that you just need to describe the structuring of configuration information. Application data shall be encapsulated by the application.  

**ProfileName**  
* The _ProfileName_ shall comply with the rules stated in [Concept of _Profiles_](../../ElementsApplicationPattern/Functions/ConceptOfProfiles/ConceptOfProfiles.md).  

**UUID**  
* The UUID shall follow the [Structure of UUIDs](../../ElementsApplicationPattern/Names/StructureOfUuids/StructureOfUuids.md).  
* Choose a meaningful _LayerID_.  
* The _ObjectType_ shall be set on "p" (_Profile_).  
* The _SequenceNumber_ shall start at "000" and must be unique within the scope of instances of _Profiles_ with the same LayerID.  

**Further Stereotypes**  
* Add the stereotypes of your _Profile_ definition.  
* Don't forget to define the attribute's value during instantiation of the application.  


### Validation and Finalization  

* Double check your _ProfileInstanceList_.  
* _Commit_ to your local feature branch.  
* _Push_ your local feature branch to the remote repository.  
* Create a _Pull-Request_.  
* Please, regard the test results of the YAML linting in the _Pull-Request_. Correct the syntax of the _ProfileList_, if errors are indicated (warnings need not to be regarded), and _commit_ and _push_ again until the _ProfileList_ in the remote repository is successfully validated.  
* Select a _Reviewer_ from the team.  
* Assign the _Pull-Request_ to yourself.  