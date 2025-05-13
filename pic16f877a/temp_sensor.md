# Temperature Sensor
// Lcd pinout settings
sbit LCD_RS at RB4_bit;\
sbit LCD_EN at RB5_bit;\
sbit LCD_D7 at RB3_bit;\
sbit LCD_D6 at RB2_bit;\
sbit LCD_D5 at RB1_bit;\
sbit LCD_D4 at RB0_bit;\
\
// Pin direction
sbit LCD_RS_Direction at TRISB4_bit;\
sbit LCD_EN_Direction at TRISB5_bit;\
sbit LCD_D7_Direction at TRISB3_bit;\
sbit LCD_D6_Direction at TRISB2_bit;\
sbit LCD_D5_Direction at TRISB1_bit;\
sbit LCD_D4_Direction at TRISB0_bit;\
\
\
float value;\
char str[16];\
void main() {\
  trisa.f0=1;\
  trisa.f1=0;\
  porta.f1=1;\
  adc_init();\
  lcd_init();\
  lcd_cmd(_lcd_cursor_off);\
  lcd_cmd(_lcd_clear);\
\
  while(1){\
  lcd_out(1, 1, "Temp =");\
  value=adc_read(0);\
  value*=0.488;\
  floattostr(value, str);\
  lcd_out_cp(str);\
   }\
    if(value>=37){\
    porta.f1=0;\
    }\
}
