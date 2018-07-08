###### import processing.serial.*;
###### Serial myPort = new Serial(this, "/dev/cu.usbmodem14341", 9600);
###### PImage img1,img2,img3;
###### boolean flag = false;

###### int yellowball = 0;
###### int count = 0;

###### void setup(){
######  size(1200,750);
######  frameRate(1);
######  background(0);
###### }

###### void mousePressed(){
######   flag = true;
###### }

###### void draw(){
###### img3 = loadImage("giphy.gif");
######         image(img3,350,250);
######   if (flag==true){
######   background(0);
######     float R = random(5,10);
######     int X = (int)random(0,9);
######     if (millis() < 60500){
######       if (X != 0){
######         yellowball++;
######         fill(255,255,0);
######         ellipse(random(1200),random(750),R,R);
######         boolean pressed = false;
######         while(myPort.available()>0){
######           char inByte = myPort.readChar();
######           println(inByte);
######          if (inByte == 'a' && pressed == false){
######             count++;
######             pressed = true;
######          }
######        }
######      }
######      else{
######        fill(0);
######        ellipse(random(1200),random(750),R,R);
######        boolean pressed = false;
######      }
######    }
######    else{
######      count++;
######      background(0); 
######      for(int i=0; i<yellowball;i++){
######        textSize(20);
######        text("the number of yellow ball",20,630);
######        fill(238,238,209);
######        ellipse(10*i+100,650,10,10);
######     }
######      for(int i=0; i<count; i++){
######        textSize(20);
######        text("click times",100,580);
######        fill(175,238,238);
######        ellipse(10*i+100,600,10,10);
######      }
######      if (yellowball == count){
######        img1 = loadImage("win.jpg");
######        image(img1,300,200);
######      }
######      else{
######        img2 = loadImage("lose.jpg");
######        image(img2,350,275);
######      }
######      fill(0, 102, 153);
######      noLoop();
######   }
######  }  
###### }
