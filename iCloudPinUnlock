/* Arduino USB HID Keyboard Demo
* Random Key/Random Delay
*/
#include <EEPROM.h>

#define KEY_LEFT_CTRL	0x01
#define KEY_LEFT_SHIFT	0x02
#define KEY_RIGHT_CTRL	0x10
#define KEY_RIGHT_SHIFT	0x20

const int KEY_0 = 0x27;
const int KEY_1 = 0x1E;
const int KEY_2 = 0x1F;
const int KEY_3 = 0x20;
const int KEY_4 = 0x21;
const int KEY_5 = 0x22;
const int KEY_6 = 0x23;
const int KEY_7 = 0x24;
const int KEY_8 = 0x25;
const int KEY_9 = 0x26;
const int KEY_ENTER = 0x28;
//const int KEY_ENTER = 0x4D;
//const int KEY_CTRL_LEFT = 0xE0;
const int KEY_CTRL_LEFT = 0x01;
const int KEY_TAB = 0x2B;
const int KEY_ESPACE = 0x2C;
int array[14] = {KEY_0, KEY_1, KEY_2, KEY_3, KEY_4, KEY_5, KEY_6, KEY_7, KEY_8, KEY_9, KEY_ENTER, KEY_CTRL_LEFT, KEY_TAB, KEY_ESPACE};
int counter = 0;
int store_adresse= 0;
byte store_value;

uint8_t buf[8] = {
  0
}; /* Keyboard report buffer */

void setup()
{
  Serial.begin(9600);
  randomSeed(analogRead(0));
  //Mouse.begin();
  delay(200);
}

void loop()
{
  delay(1000);
  counting();
}

void releaseKey()
{
  buf[0] = 0;
  buf[2] = 0;
  Serial.write(buf, 8); // Release key
}

void tip(int i) {
  delay(100);
  buf[0] = 0;
  buf[2] = array[i]; // letter R
  Serial.write(buf, 8);
  releaseKey();
  delay(100);
}

void tipCombo(int i, int j) {
  delay(100);
  buf[0] = array[i];
  buf[2] = array[j]; // letter R
  Serial.write(buf, 8);
  releaseKey();
  delay(100);
}

void counting() {
  for (int a = 0; a < 10; a++) {
    for (int b = 0; b < 10; b++) {
      for (int c = 0; c < 10; c++) {
        for (int d = 0; d < 10; d++) {
          counter++;
          //  if ((a == 0)||((a==1)&&(b<2))){
          //  if ((a == 0) || ((a == 1) && (b < 8))) {
          if (((a <2)||((a==2)&&(b<8)))) {
            continue;
          }
          tip(a);
          delay(32);
          tip(b);
          delay(120);
          tip(c);
          delay(200);
          tip(d);
          delay(30);
          tip(10);
          delay(50);

          
          if (counter % 5 == 0) {
            tipCombo(11, 12);
            tipCombo(11, 12);
            tipCombo(11, 12);
            tip(13);
            delay(32000);
          }
          else {
            delay(1000);
          }
        }
      }
    }
  }
}
