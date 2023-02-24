/***************************************************************
*Corresponding Device: Athom Tasmota 3 Way Relais              *
*Description: This Rule turns Power1 (lights) on for 90sec on a*
*short  press on the button. WHen you hold the Button for at   *
*least 2sec, this rule will turn on the light until the button *
*is hold again for 2sec (or after 90sec when the button was    *
*shortly pushed                                                *
*                                                              *
*Prerequisites: You need to change the Template of the device  *
*as follows:                                                   *
*Change the Switch1 on GPIO14 to Button2                       *
*Rule execution has to be single line (except SetOption)       *
*Formatted it for better readability                           *
***************************************************************/

SetOption32 20 /* HOLD Time in 0.1 SEC */
Rule1 
	ON button2#state=2 DO Backlog Power1 on; RuleTimer1 90 ENDON  
	ONRules#Timer=1 DO Power1 off ENDON 
	ON button2#state=3 DO Power1 TOGGLE ENDON
Rule1 1
