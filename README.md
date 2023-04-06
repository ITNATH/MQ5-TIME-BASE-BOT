 
#property copyright "Copyright 2023, MetaQuotes Ltd."
#property link      "https://www.mql5.com"
#property version   "1.00"

//+------------------------------------------------------------------+
//| Expert initialization function                                   |
//+-----------------------------------------------------------
#include <Trade\Trade.mqh>



//+------------------------------------------------------------------+
//| Expert initialization function                                   |
//+------------------------------------------------------------------+
  input int openHour; 
  input int closerHour;
  bool IsTradeOpen = false;
  CTrade trade;





//+------------------------------------------------------------------+
//| Expert initialization function                                   |
//+------------------------------------------------------------------+
int OnInit(){

     //check user input
     if(openHour == closerHour){
        Alert("openHour and closerHour must differ");
        return INIT_PARAMETERS_INCORRECT;
     }

   return(INIT_SUCCEEDED);
  }
//+------------------------------------------------------------------+
//| Expert deinitialization function                                 |
//+------------------------------------------------------------------+
void OnDeinit(const int reason)
  {

   
  }
//+------------------------------------------------------------------+
//| Expert tick function                                             |
//+------------------------------------------------------------------+
void OnTick() {

    //get current time
  MqlDateTime timeNow;
  TimeToStruct(TimeCurrent(),timeNow);
  
// check for trade open
   if (openHour == timeNow.hour && !IsTradeOpen){
   
   // position open
   trade.PositionOpen (_Symbol, ORDER_TYPE_BUY, 1, SymbolInfoDouble(_Symbol, SYMBOL_ASK), 0, 0);


  // set flag
  IsTradeOpen = true;
  
   }
   
    // check for trade open
   
   if (closerHour == timeNow.hour && IsTradeOpen){
   
   // position open
   trade.PositionClose (_Symbol);


  // set flag
  IsTradeOpen = false;
   
      }
  }
