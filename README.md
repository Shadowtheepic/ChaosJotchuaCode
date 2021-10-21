// Demonstrate primitve drawing in SFML
// Headers

using namespace std;


#include "SFML/Graphics.hpp"
#include "SFML/Audio.hpp"

//2D matrix in SFML
#include<iostream>
using namespace std;


class fish {
private:
    int xpos;
    int ypos;
    int xvel;
    int yvel;
    char color;
    bool isdead;
    bool onhook;
public:
    fish();
    void moving();
    void printing();

};

int main() {
    char input;

    


    vector<fish> fishes;
    vector<fish>::iterator fishies;
    //instantiate 3 goombas:
    fish f1;
    fish f2;
    fish f3;
    fishes.push_back(f1);
    fishes.push_back(f2);
    fishes.push_back(f3);
    do {//game loop

        for (fishies = fishes.begin(); fishies < fishes.end(); fishies++) {
            (*fishies).moving();
            (*fishies).printing();
            sf::RenderWindow renderWindow(sf::VideoMode(500, 500), "Quiz"); //set up screen
            sf::Event event; //set up event queue
            sf::Texture texture;
            sf::Sprite sprite;
            sf::Texture texture2;
            sf::Sprite sprite2;
            

            texture.loadFromFile("jotchua.jpg");
            texture2.loadFromFile("Jotchualooking.jpg");


            while (renderWindow.isOpen()) {
                while (renderWindow.pollEvent(event)) {
                    if (event.type == sf::Event::EventType::Closed)
                        renderWindow.close();
                    sprite.setTexture(texture);
                    sprite2.setTexture(texture2);
                    renderWindow.clear(); //wipes screen, without this things smear
                    renderWindow.draw(sprite);
                    renderWindow.display();
                    renderWindow.draw(sprite2);
                    renderWindow.display();
                    //flips memory drawings onto screen

                }//thanks for dn

            }
        }

       
        cout << endl << "press any key to run again, 'q' to quit" << endl;
        cin >> input;
    } while (input != 'q');

    

    sf::CircleShape shape(50);
    shape.setFillColor(sf::Color(227, 66, 52));
    shape.setPosition(215.0f, 160.0f);
    sf::RectangleShape paddle1(sf::Vector2f(20.0f, 100.0f));
    paddle1.setFillColor(sf::Color::Green);
    paddle1.setPosition(250.0f, 250.0f); //set position: this is where the top left corner will be

    sf::RenderWindow renderWindow(sf::VideoMode(500, 500), "Quiz"); //set up screen
    sf::Event event; //set up event queue
    sf::Texture texture;
    sf::Sprite sprite;
    texture.loadFromFile("jotchua.jpg");

    while (renderWindow.isOpen()) {
        while (renderWindow.pollEvent(event)) {
            if (event.type == sf::Event::EventType::Closed)
                renderWindow.close();
            sprite.setTexture(texture);
            renderWindow.clear(); //wipes screen, without this things smear
            renderWindow.draw(sprite);
            renderWindow.display(); //flips memory drawings onto screen

        }
    }//my code now

}


fish::fish() {
    int ran = rand() % 500;
    int alran = rand() % 500;
    xpos = ran;
    ypos = alran;
    xvel = 0;
    yvel = 0;
    color = 'g';
    isdead = 0;
    onhook = 0;
}

void fish::moving() {
    int mov = rand() % 6 - 3;
    xvel = mov;
    yvel = mov;

    ypos += xvel;
    yvel += yvel;
}

void fish::printing() {
    cout << "the fish is currently at: " << xpos << " " << ypos << " and looks like "<< endl;

}
