#include <iostream>
#include <string>
#include <fstream>
using namespace std;

string positive_words[500] = { "admiration","love","like","good","positive","happy", "adoration", "affection", "amazement", "amusement", "anticipating", "assertive", "attraction", "joyful", "kind", "awesome", "fantastic", "amazing", "excellent", "grateful", "wonderful", "uplifting", "lovely", "optimistic", "benevolent", "cheerful", "radiant", "delightful", "ecstatic", "elated", "exuberant", "glorious", "heartwarming", "inspiring", "jovial", "lively", "magnificent", "marvelous", "miraculous", "pleasurable", "serene", "spectacular", "splendid", "superb", "terrific", "upbeat", "vibrant", "vivacious", "amiable", "blissful", "captivating", "charming", "content", "elegant", "enthusiastic", "harmonious", "innocent", "jubilant", "rapturous", "sensational", "wholesome"};
string negative_words[500] = { "angry","hate","bad","depressed","dont","sad", "miserable", "unhappy", "pessimistic", "negative", "upset", "frustrated", "disappointed", "anxious", "stressed", "scared", "worried", "fearful", "jealous", "envious", "bitter", "resentful", "hostile", "lonely", "isolated", "alone", "abandoned", "neglected", "worthless", "inferior", "ugly", "unattractive", "disgusting", "stupid", "dumb", "unintelligent", "ignorant", "incompetent", "failure", "useless", "unimportant", "insignificant", "meaningless", "pathetic", "pitiful", "weak", "helpless", "hopeless"};
string substring[100];
string input;
 
int positive_count = 0, negative_count = 0, word_count = 0, substring_index = 0;

void inputarray()
{
	word_count = 0;
	substring_index = 0;

	//storing input in to an array
	for (int i = 1; i < input.length(); i++)
	{
		if (input[i] == ' ' || input[i] == '\t' || input[i] == '\n')
		{
			word_count++;
			 
			substring[substring_index++] = input.substr(0, i);
			input = input.substr(i + 1);     //resets substring starting position....exclude proceeded word
			i = -1;                          // will reset the loop to start from start
		}
	}
}

void convert_lower()
{
	//loop for converting every character to lowercase
	for (int i = 0; i < substring_index; i++)
	{
		for (char& c : substring[i])
		{
			c = tolower(c);
		}
	}
}

void comparring_arrays() 
{
	//comparring input array with postive word array
	for (const string& word : positive_words) {
		string currentWord = word;

		for (int i = 0; i < substring_index; i++)
		{
			if (substring[i] == currentWord)
			{
				positive_count++;
			}
		}
	}

	//comparring input array with negative word array
	for (const string& word : negative_words) {
		string currentWord = word;

		for (int i = 0; i < substring_index; i++)
		{
			if (substring[i] == currentWord)
			{
				negative_count++;
			}
		}
	}
}

int main()
{
	char choice;
    int option;
	do
	{
		ofstream record;
		record.open("record.txt", ios::app);

		cout << "====================== Sentiment Analysis =========================" << endl;
		cout << "[1] Start " << endl;
		cout << "[2] Record " << endl;
		cout << "[3] Exit " << endl;
		cin >> option;

		if (option == 1)
		{
			cin.ignore();

			cout << "Enter input for analysis :" << endl;
			getline(cin, input);

			inputarray();
			convert_lower();
			comparring_arrays();

			cout << "Positive Words :" << positive_count << endl;
			cout << "Negative Words :" << negative_count << endl;

			if (positive_count > negative_count) {
				cout << "Positive Feed back" << endl;
				record << "Positive feed back" << endl;
			}

			else if (negative_count > positive_count)
			{
				cout << "Negative Feed back" << endl;
				record << "Negative feed back " << endl;
			}

			else
			{
				cout << "Neutral Feed back" << endl;
				record << "Neutral Feed back " << endl;
			}

			record.close();
		}

		else if (option == 2)
		{
			int pos_feedback = 0, neg_feedback = 0, neut_feedback=0 ;

			string feedback;
			ifstream record;
			record.open("record.txt");
			while (getline(record, feedback))
			{
				cout << feedback << endl;
				if (feedback.size() >= 8 && feedback.substr(0, 8) == "Positive")
				{
					pos_feedback++;
				}
		
				else if (feedback.size() >= 8 && feedback.substr(0, 8) == "Negative")
				{
					neg_feedback++;
				}
		
				else
				{
					neut_feedback++;
				}
			}

			cout << "================ Feedback Ratio ================" << endl;
			cout << "Total Feedbacks: " << pos_feedback + neg_feedback + neut_feedback << endl;
			cout << "Positive Feedbacks: " << pos_feedback << endl;
			cout << "Negative Feedbacks: " << neg_feedback << endl;
			cout << "Neutral Feedbacks: " << neut_feedback << endl;
			cout << "=================================================" << endl;

			record.close();
		}

		else if (option == 3)
		{
			cout << "Exiting the program ..." << endl;
			return 0;
		}

		else
		{
			cout << "Option not in the list " << endl;
		}

		cout << endl << "====================================================================================" << endl;
		cout << "Go to the menu ? (Y/Any key)" << endl;
		cin >> choice;

		positive_count = 0;
		negative_count = 0;
	}
	while (choice=='Y' || choice=='y');

	return 0;
}
