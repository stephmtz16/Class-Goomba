# Class-Goomba
goomba 

#include<iostream>
#include<allegro5/allegro.h>
#include<allegro5/allegro_primitives.h>
#include<allegro5/allegro_image.h>
using namespace std;

class Goomba {
private:
	string name;
	int color;
	ALLEGRO_BITMAP* blue;
	ALLEGRO_BITMAP* brown;
	int xpos;
	int ypos;

public:
	void initialize(int x, int y, int c, string n, ALLEGRO_BITMAP *pic1, ALLEGRO_BITMAP *pic2);
	void print();
	void draw();

};

int main() {

	al_init();
	al_init_primitives_addon();
	al_init_image_addon();
	
	ALLEGRO_DISPLAY* display = al_create_display(1500, 1500);
	ALLEGRO_BITMAP* p1 = al_load_bitmap("goomba1.jpg");
	ALLEGRO_BITMAP* p2 = al_load_bitmap("blue.jpg");
	//add the second one

	Goomba ally;
	ally.initialize(200, 200, 0, "bob",  p1, p2);
	ally.print();
	ally.draw();

	Goomba kevin;
	kevin.initialize(50, 800, 0, "billy", p1, p2);
	kevin.print();
	kevin.draw();

	Goomba bob;
	bob.initialize(100, 350, 1, "bil", p1, p2);
	bob.print();
	bob.draw();

	Goomba bird;
	bird.initialize(520, 580, 1, "bab", p1, p2);
	bird.print();
	bird.draw();

	al_flip_display();
	al_rest(55);
}
void Goomba::initialize(int x, int y, int c, string n, ALLEGRO_BITMAP* pic1, ALLEGRO_BITMAP* pic2) {
	xpos = x;
	ypos = y;
	color = c;
	brown = pic1;
	blue = pic2;
	name = n;
}
void Goomba:: draw() {
	if (color == 0)
		al_draw_bitmap(brown, xpos, ypos, NULL);
	else
		al_draw_bitmap(blue, xpos, ypos, NULL);
}

void Goomba::print() {

	cout << "My name is " << name << endl;
	if (color == 0)
		cout << "You chose the browm goomba " << endl;
	else
		cout << "You chose the blue goomba" << endl;

}
