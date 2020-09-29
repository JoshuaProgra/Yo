Spot sp1, sp2, sp3; // Declare the objects
void setup() {
  size(100, 100);
  smooth();
  noStroke();
  sp1 = new Spot(10, 50, 40, 0.5); // Construct sp1
  sp2 = new Spot(60, 50, 30, 1.5); // Construct sp3
}
void draw() {
  fill(0, 15);
  rect(0, 0, width, height);
  fill(255);
  sp1.move();
  sp2.move();
  sp1.display();
  sp2.display();
}

class Spot {
  float x, y; // X-coordinate, y-coordinate
  float extent; // width and height of the rectangle
  float speed; // Distance moved each frame
  int direction = 1; // Motion Direction(1 is down, -1 is up)
  Spot(float xpos, float ypos, float ext, float sp) {
    // Constructor
    x = xpos;
    y = ypos;
    extent = ext;
    speed = sp;
  }
  void move() {
    y += (speed * direction);
    if ((y > (height - extent / 2)) || (y < extent / 2)) {
      direction *= -1;
    }
  }
  void display() {
    square(x, y, extent);
  }
}
