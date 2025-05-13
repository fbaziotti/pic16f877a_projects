ADC_init();\
int duty;\
int x;

void main() {

  PWM1_init(1000);//frequency\
  pwm1_start();
  
  trisb.f0=0;\
  trisb.f1=0;\
  portb.f0=0;\
  portb.f1=0;
  
  while(1){

     x=adc_read(0);
     duty=(x/4);
     pwm1_set_duty(duty);
     portb.f0=1;
     portb.f1=0;
     delay_ms(5000);
     portb.f0=0;
     portb.f1=1;
     delay_ms(5000);
     }
   }
