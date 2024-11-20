## EOP🐶

### how to input eof

### the cin object are disabled after EOF is inputted(WIP)
int main()
{
    string word;
    int num;
    vector<string> words;
    vector<int> nums;
    while (cin >> word)
    {
        words.push_back(word);
    }
    cout << "words end" << endl;

    // while (cin >> word)
    // {
    //     words.push_back(word);
    // }
    cin.clear();
    while (cin >> num)
    {
        nums.push_back(num);
    }
    cout << "nums end" << endl;
    return 0;
}