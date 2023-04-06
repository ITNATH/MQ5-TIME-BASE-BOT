# MQ5-TIME-BASE-BOT


#property copyright "Copyright 2023, MetaQuotes Ltd."
#property link "https://www.mql5.com"
#property version "1.00"

//+------------------------------------------------------------------+
//| INPUT |
//+------------------------------------------------------------------+

input int InpRangeStart = 600; //range start time is minutes after mid -night
input int InpRangeDuration = 120; // range duration in minutes
input int InpRangeClose = 1200; //range close time in minutes
input double InpLots = 0.01; // lot side
input long InpMageicNumber = 12345; // magic number

//+------------------------------------------------------------------+
//| Expert initialization function |
//+------------------------------------------------------------------+
int OnInit(){

if(InpMageicNumber <= 0){
Alert("MageicNumber <= 0");
return INIT_PARAMETERS_INCORRECT;
}
if(InpLots <= 0 || InpLots > 1){
Alert("lots <= 0 or > 1");
return INIT_PARAMETERS_INCORRECT;
}
if(InpRangeStart <= 0 || InpLots >= 1440){
Alert(" Range start < 0 or >= 1440");
return INIT_PARAMETERS_INCORRECT;
}

if(InpRangeDuration <= 0 || InpRangeDuration >= 1440){
 Alert(" Range start < 0 or >= 1440");
 return INIT_PARAMETERS_INCORRECT;
}

if(InpRangeClose <= 0 || InpRangeClose >= 1440 || (InpRangeStart+InpRangeDuration)%1440 == InpRangeClose){
 Alert("Close time < 0 or >= 1440 or end time == close time");
 return INIT_PARAMETERS_INCORRECT;
}

return(INIT_SUCCEEDED);
}

//+------------------------------------------------------------------+
//| Expert deinitialization function |
//+------------------------------------------------------------------+
void OnDeinit(const int reason)
{

}

//+------------------------------------------------------------------+
//| Expert tick function |
//+------------------------------------------------------------------+
void OnTick()
{

}
 
