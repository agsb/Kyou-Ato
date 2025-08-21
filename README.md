# Kyou Ato

__After Today__

Kyou Ato is a easy personal *Kan-Ban*. 

It's manages an list of tasks, that can be ordened top-down by high to low priority and selected by dates or states.

Highlight the first five tasks and shows blocks of 20 to 20 tasks, 

## Cards

The tasks are keeped in a list of cards with

    "List" : {
      "Order" : "  ",
      "Uuid" : " ",
      "Next" : "  "
      }
      
    "Card" : {
      "Uuid" : " ",
      "State" : " ",
      "Time0" : " ",
      "Time1" : " ",
      "Time2" : " ",
      "Time3" : " ",
      "Title" : " ",
      "Notes" : " "
      }

In format of CSV or JSON, one entry by line, List (order, uuid), Task (uuid, time0, time1, time2, time3, title, notes)

  Order is the ordinary sequence ;
  
  Uuid is the classic UUID ;
  
  State is one of ( 1 TODO, 2 WORK, 3 DONE, 0 HOLD ). 
      A task in TODO is waiting to start, in WORK is in progress, in DONE is finished. 
      A task in HOLD is waiting some external resource, or action or event, and ;
  
  Time0, Time1, Time2, Time3 are time in YEAR.MOUNTH.DAY. 
      Time0 is when task goes into list, 
      Time1 is when task starts, 
      Time2 is when task is done, 
      Time3 is the deadline of task;

  Title is a text of less than 120 characters.

  Notes is a small text with a URI to the notebook ;

## Does

the cards could be sorted based on specifics per data, per state, etc


  

