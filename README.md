# MVVM-Generator

---
## Types
### Basic types:
- **integer[8|16|32|64]** size suffix may be excluded, and 64 is the default.
- **double[32|64]** size suffix may be excluded, and 64 is the default.
- **boolean** 
- **character** 
- **string** 
- **complex[32|64]** size suffix may be excluded, and 64 is the default.

### Objects
- **object** *name*: 

to define a new object.

- **object** *model_name*

to utilize a previously defined model.

### Collections:
- **[]type** for an array or list
- **{}type** for a set
- **{basic_type}type** for a map from basic_type to type

### Optional Types:
For a field that is optional (i.e. may or may not exist in the model), add the **optional** flag after the type.


## Client Scheme
First, define models (optional)

**model** *model_name*:  
&nbsp;&nbsp;&nbsp;&nbsp;...  

Next, define services

**service** *name*  
&nbsp;&nbsp;&nbsp;&nbsp;**model** *model_name*  
&nbsp;&nbsp;&nbsp;&nbsp;**model** *api_model_name*:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**type** **[optional]** *name*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**object** **[optional]** *name*:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**object** **[optional]** *model_name*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...  

&nbsp;&nbsp;&nbsp;&nbsp;**method [local|remote]** *name*(*poll_data*) *api_model_name|model_name*

Then, define repositories

**repository** *name*  
&nbsp;&nbsp;&nbsp;&nbsp;**service** *service_name*  

&nbsp;&nbsp;&nbsp;&nbsp;**model** *model_name*  
&nbsp;&nbsp;&nbsp;&nbsp;**model** *domain_model_name*:   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...  

&nbsp;&nbsp;&nbsp;&nbsp;**method** *name*(*method_arguments*) *domain_model_name|model_name*  

Finally, define views

**view** *name*  
&nbsp;&nbsp;&nbsp;&nbsp;**repository** *repository_name*  

&nbsp;&nbsp;&nbsp;&nbsp;**model** *model_name*  
&nbsp;&nbsp;&nbsp;&nbsp;**model** *view_model_name*:   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...  

&nbsp;&nbsp;&nbsp;&nbsp;**command** *name*   
