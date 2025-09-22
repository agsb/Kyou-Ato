# Kyou Ato

__After Today__

Kyou Ato (今日 後) is an easy personal *Kan-Ban*. 

It's manages only one list of tasks, that can be ordened top-down by high to low priority and selected by dates or states.

Highlight the first five tasks and shows blocks of 20 to 20 tasks.

Think in Post-Its with steroids.

## Cards

The tasks are keeped in a list of cards with
     
    "Task" : {
      "Uuid" : " ",
      "Order" : " ",
      "Notes" : " "
      "State" : " ",
      "Time0" : " ",
      "Time1" : " ",
      "Time2" : " ",
      "Time3" : " ",
      "Title" : " ",
      }

In format JSON or CSV, one entry by line, Task (uuid, order, time0, time1, time2, time3, title, notes) ;

Order is the ordinary sequence ;
  
  Uuid is the classic UUID ;
  
  State is one of ( 1 TODO, 2 TASK, 3 DONE, 0 HOLD ). 
      A task in TODO is waiting to start, in TASK is in progress, in DONE is finished. 
      A task is in HOLD while waiting some external resource, or action or event, and will return to WORK ;
  
  Time0, Time1, Time2, Time3 are time in YEAR.MOUNTH.DAY. 
      Time0 is when task goes into list, 
      Time1 is when task starts, 
      Time2 is when task is done, 
      Time3 is the deadline of task ;

  Title is a text of less than 120 characters ;

  Notes is a small text with a URI to the notebook ;

## Does

the cards are only sorted by user, moving cards top-down.
    At top is most priority and sort order is always preserved ;

the cards could be select by states or not states ;

the cards could be selected based per due data ;

eventualy cards could have colors ;

## Metrics

the mean interval time (days) between 
    TODO and TASK, TASK and DONE, TODO and DONE ;

the mean quantity of tasks inside each interval ;



  

