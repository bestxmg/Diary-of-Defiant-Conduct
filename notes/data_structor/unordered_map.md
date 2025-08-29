## how to make a non-hashable element into the key of unordered_map
struct pairHash{
    size_t operator()(pair<int, int> p){
        size_t hashkey = hash<int>{}(p.first);

        hashkey ^= (hash<int>{}(p.second) << 1);
        return hashkey; 
    }
};
#define HALF_INT_MAX INT_MAX / 2
int tsp(const vector<vector<int>>& cost) {
    int sz = cost.size();
    int allVisited = (1 << sz) - 1;
    unordered_map<pair<int, int>, int, pairHash> dp;
    for (int i = 1; i <= allVisited; ++i)
    {
        for (int j = 1; j <= sz; ++j)
        {
            dp.insert({{i,j}, HALF_INT_MAX});
        }
    }
    return INT_MAX;
}
};