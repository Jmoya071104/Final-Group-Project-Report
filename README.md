Project Report: NBA Team and Players Stat Tracker
1. Overview
   
1.1 Background Information

This project was created to display our understanding of various C++ object-oriented concepts.
This application is designed to provide a quick and efficient way to organize and view various statistics and rankings from last year's NBA season.

Our project uses accurate information (gathered from the NBA's own site) and displays it in a simple yet effective manner that allows even beginners in the sport to stay updated on the league's best teams and players.

2. Technical Details

2.1 Object-Oriented Programming Concepts Used

This project used a variety of object-oriented and C++ concepts.

-Functions/methods:
  Throughout the project, a variety of methods were developed and employed to gather and return information. An example of this is shown within our classes through the use of getters, which allowed the program to display attributes belonging to specific objects.
    -Example Code:
    
    std::string getName() {
    return name;
    }

-Classes and objects:
  The final version of this project included four different classes, each containing its own
  unique attributes and methods.
    -Example Code:
```    
class Players {
public:
    std::string name;
    float gamesPlayed;
    double ppg;
    double apg;
    double rpg;

    Players() {
        name = "";
    }

    Players(std::string name, double ppg, double apg, double rpg, float games) {
        this->name = name;
        this->ppg = ppg;
        this->apg = apg;
        this->rpg = rpg;
        this->gamesPlayed = games;
    }

    std::string getName() {
        return name;
    }
};
```

-Encapsulation:
  The concept of encapsulation was demonstrated multiple times throughout the project through the use of access specifiers, such as public, private, and protected.

-Inheritance:
  The "Team" class served as a base class for two subclasses ("EasternTeam" and "WesternTeam),    making it an example of hierarchical inheritance; this concept was exceptionally useful as it allowed for the reusing of attributes without the need to repeat parts of code.

-Polymorphism:
  The "Team" class, as presented in the code, includes a purely virtual function; therefore, it is necessary to use function overriding in its derived classes. This allowed for a more dynamic use of pointers, as it enabled the proper function to be used depending on the object being used.
  
    Example code:
```
    class Team {
public:
    std::string name;
    Players lineup[5];
    int ranking;

    Team(std::string name, Players players[5], int ranking) {
        this->name = name;
        for (int i = 0; i < 5; i++) {
            this->lineup[i] = players[i];
        };
        this->ranking = ranking;
    };

    virtual int ConferenceRanking() = 0;
};
```

-Abstraction:
  As stated above, one of our classes contained a purely virtual function, meaning that it automatically forced itself to be an abstract class, making it useful as a template for its subclasses.

-Arrays: 
  Due to the large amount of data that this application handles, the most efficient way to store it was to use multiple arrays. An array of players was implemented to keep track of each team's lineup. Furthermore, arrays were also used with buttons and labels to edit the details of each component quickly.

2.2 Framework used.
  The entirety of this project was created using WinForms for both its GUI and C++ components. WinForms was used because it allowed for the best blend between GUI and C++; additionally, due to its straightforward implementation, it was very accessible to every member of the group, which promoted a collaborative atmosphere.


3. References and Citations

-The most helpful source of information throughout this project was the YouTube playlist provided in Canvas about WinForms.
Link: https://www.youtube.com/playlist?list=PL2i17lRog5pBe7t9zJdFdugQ6bxgjntJD

-Another helpful site was "StackOverflow", which is a collaborative online site where thousands of programmers can post questions and receive answers from anyone, ranging from experts to beginners. Furthermore, the site features an archive of hundreds of previously asked questions, making it easy to find information on a wide range of topics.
Link: https://stackoverflow.com/questions


4. Analysis and Reflection

4.1 Challenges and Solutions
As this was our first time using the WinForms framework, a variety of issues emerged when we attempted to create our project. For starters, due to our inexperience with the framework, our first attempt at the project was riddled with bugs; furthermore, it was written in a very messy, illegible manner. However, as time passed and we became more comfortable with the framework, we were able to reorganize our initial code, making it much easier to understand.
Once the code was more understandable, debugging became much simpler as we no longer had to pick through hundreds of lines to find an issue.

Another problem we faced was the time-consuming process of manually drawing each button and label onto the page. To solve this, we decided to dynamically create the page components at runtime by utilizing arrays. For example, in the "TeamSelectPage", there are a total of 30 buttons, which would have taken hundreds of lines of code to write if we decided to do this manually; however, through the use of a 2d array, a loop was able to quickly draw each button in its corresponding position in a fraction of the time. Furthermore, since the loop consisted of only 20 lines, it was much easier to understand.

for (int row = 0; row < 5; row++) {
	for (int column = 0; column < 6; column++) {
		buttons[row,column]->Location = Point(Hspacing * (column+1) + column * btnLenght , fromTop + row*Vspacing + row*btnHeight);
		buttons[row, column]->Name = gcnew String(teamBtnNames[nameIndex].c_str());
		buttons[row, column]->Size = System::Drawing::Size(btnLenght, btnHeight);
		buttons[row, column]->TabIndex = tabIndex;
		tabIndex++;
		buttons[row, column]->Text = gcnew String(teamNames[nameIndex].c_str());
		buttons[row, column]->Font = gcnew System::Drawing::Font(buttons[row, column]->Font->FontFamily, fontSize - 5, FontStyle::Bold);
		buttons[row, column]->ForeColor = Color::Red;
		buttons[row, column]->UseVisualStyleBackColor = true;
		buttons[row,column]->Click += gcnew System::EventHandler(this, &SelectTeamPage::anyTeam_Click);
		buttons[row,column]->BackgroundImage = Image::FromFile(gcnew String(nbaLogos[nameIndex].c_str()));
		nameIndex++;
		buttons[row, column]->BackgroundImageLayout = ImageLayout::Zoom;
		buttons[row, column]->Cursor = Cursors::Hand;
		Controls->Add(buttons[row, column]);
	}
}

4.2 Future Improvements
A significant limitation of this application is that it is only capable of displaying player stats for the starting lineups of each team, meaning that for every team, there are ten players whose stats are not available. In the future, we will be able to showcase every player's stats.
