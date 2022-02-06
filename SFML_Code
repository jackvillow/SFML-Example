#include <iostream>
#include <SFML/Graphics.hpp>
#include <cmath>


using namespace std;
using namespace sf;


int winHeight = 1000, winWidth = 1500;

int iter = 400;
double a = -50, b =50;
double kx, bx, ky, by, xZero, yZero;

double MFunc(double x) {
	return x*x-100;
}


void Graph(RenderWindow& wndw) {
	VertexArray func(LineStrip, iter);
	for (int i = 0; i < iter; i++) {
		double verx = a + i * (b - a) * 1.0 / (iter);
		func[i].position.x = verx;
		func[i].position.y = MFunc(func[i].position.x)*ky+by;
		func[i].position.x = func[i].position.x * kx + bx;
		func[i].color = Color::White;
	}
	wndw.draw(func);
}

void Axe(RenderWindow& Wndw, double yZero, double xZero) {
	VertexArray xAxis(Lines, 2);
	xAxis[0] = Vector2f(0, yZero);
	xAxis[1] = Vector2f(winWidth, yZero);
	xAxis[0].color = Color::Green;
	xAxis[1].color = Color::Green;

	VertexArray yAxis(Lines, 2);
	yAxis[0] = Vector2f(xZero, winHeight);
	yAxis[1] = Vector2f(xZero, 0);
	yAxis[0].color = Color::Green;
	yAxis[1].color = Color::Green;

	Wndw.draw(xAxis);
	Wndw.draw(yAxis);

}


int main() {
	double maxY, minY, dMaxY, dMinY;
	RenderWindow Wndw(VideoMode(winWidth, winHeight), "Graph");
	maxY = MFunc(a);
	minY = maxY;
	
	for (int i = 0; i < iter; i++) {

		if (maxY < MFunc(a + i * (b - a) * 1.0 / (iter))) 
			maxY = MFunc(a + i * (b - a) * 1.0 / (iter));

		if (minY > MFunc(a + i * (b - a) * 1.0 / (iter))) 
			minY = MFunc(a + i * (b - a) * 1.0 / (iter));

	}
	kx = winWidth * 1.0 / (b - a);
	bx = -a * kx;
	ky = winHeight * 1.0 / (minY - maxY);
	by = -maxY * ky;
	xZero = bx;
	yZero = by;
	cout << xZero << "  " << yZero;
	//Wndw.display();
	while (Wndw.isOpen())
	{
		Event e;
		while (Wndw.pollEvent(e))
		{
			if (e.type == Event::Closed)
				Wndw.close();
		}
		Graph(Wndw);
		Axe(Wndw, yZero, xZero);
		Wndw.display();
	}
}
