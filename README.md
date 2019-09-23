# catalog-select
Wrapper for Material design md-select


## Description

This components implements the angular componentes directive "md-select" and performs all the catalog handling logic with pagination and soft delete, it just requires a JS object (described below) for doing so.


## Requirements

AngularJS > v1.6.4
Angular Material >v0.5.1
https://github.com/angular/components


## Usage

Below is a description of the parameters required by the component

       catalog:{
           url: string,                 Without query or pagination parameters
           query: string,               (Optional) query to be used if the catalog depends of other
                                        In this component it must be received without the value
                                        to use directly in the API.
                                        Example: ?parameter_name=
           query_value:string,          (Optional) Value tu search on the API with the given query.
           name: string,                (Optional) Default is "Catalog"
           loadMoreButtonText, string   (Optional) Test to show in the 'Load more' Button, default is 'Load more'
           model: string,               From the catalog object, which element will be sent (aka: id, name, etc.)
           option: string,              (Optional) From the catalog object, which element will be shown in the list (ake: name,       description, etc)
                                       If not given, then the model will be used.
          showModel: boolean,          (Optional) If given, the model and the option will be shown with the following template
                                       <b>{{model}}</b> - {{option}}
          elements: string,     (Optional) Model used if the elements are not returned at the root of the response
                            aka: the API returns the array of objects in an element of the response, as in pagination
                            Example:
                            {
                              total:'',
                              description:'',
                              results:[
                                  {...},
                                  {...}
                              ]
                            }
                            In this case 'elements' should receive the parameter 'results'
          pagination: {         (Optional) If present, the component asumes that the catalog API uses pagination
          //Next parameter, just used when the url is going to be used from what the API returned.
              next: string,         (Optional) Binding for the url that brings to the next page
          //Total, limit and offset, used when the component is going to calculate and build the query,
          //All of the following are required if no next parameter is given.
              total: string,        (Optional) Binding for the number of total elements.
              limit: string,        (Optional) Parameter used for the query building, not the number.
              offset: string,       (Optional) Parameter used for the query building, not the number.
              pageSize: number      (Optional) Used to determine how many results are going to be loaded per page.
          },
          softDelete: {
              hide: string,         Boolean property to consider in order to hide the element (hide, deleted, disabled, etc.)
              reverse: boolean      If true, the element will be hiden when the parameter is false rather than true
          },
      },
      hint: string,         (Optional) Shows a message under the field
      icon: string,         (Optional) Shows an icon from FontAwesome or ZMDI
      lock: boolean,        (Optional) If given the catalog select will be disabled
      required: boolean,    (Optional) To be used in form validation
      lazy: boolean,        (Optional) If given, the catalog won't load until the selector is opened
      
      initial:string,       (Optional) Must be the ID you want to be selected (if single)
                            Must be the elements selected with ID and option (if multiple)
                            Iy nulls the lazy parameter
      showModel:boolean,    (Optional) Allows to shoe the model and the option of the catalog with the following format
                            <b>{{model}}</b> - {{option}}
      multiple:boolean,     (Optional) Allows to select more than one element.
      noResults: string     (Optional) Used when the url return a 0 length array, default is "No results" 
      
      
      
##Use the component directly as an html element directive:

    <catalog-select></catalog-select>
