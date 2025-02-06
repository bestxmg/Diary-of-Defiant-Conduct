max_element
abs
std::equal(elements, first_free, s.elements)
std::lexicographical_compare(lhs.begin(), lhs.end(), rhs.begin(), rhs.end())
 std::replace_if(vec.begin(), vec.end(), IsEqual(3), 5);

 make_heap(arr.begin(), arr.end(), greater<int>());

 iter_swap(arr.begin(), arr.begin() + unSortedIndex);

sort an array
    std::sort(arr, arr + n, [](int a, int b) {
        return a > b;  // Change the order to descending
    });


## find specific element from end to begin
        auto rend = find_if(arr.rbegin(), arr.rend(), [](int x){return x > 0;});
        auto end = rend.base() - 1;


## merge two sets
set_intersection



## move Iterator
std::unordered_set<int> uset;
    uset.insert(std::make_move_iterator(vec.begin()), std::make_move_iterator(vec.end()));

WIP