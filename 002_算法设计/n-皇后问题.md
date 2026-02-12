Cpp 写法 

```cpp

class Solution {
private:
    int n;
    vector<bool> cols;
    unordered_map<int, bool> diagonal_pos;
    unordered_map<int, bool> diagonal_neg;
    vector<pair<int, int>> path;
    vector<vector<string>> ans; // 最终翻译成字符串的结果

public:
    vector<vector<string>> solveNQueens(int n) {
        this->n = n;
        cols.assign(n, false);

        // 递归求解
        dfs(0);

        return ans;
    }

    void dfs(int i) { // i表示第几行，如果到了n行说明就是一个答案，其余情况如果都不符合就会自动结束
        if (i == n) {
            ans.push_back(build(path));
        }

        for (int j = 0; j < n; j++) {
            if (!cols[j] && !diagonal_pos[i - j] && !diagonal_neg[i + j]) {
                cols[j] = true;
                diagonal_pos[i - j] = true;
                diagonal_neg[i + j] = true;
                path.push_back({i , j});

                dfs(i + 1);

                cols[j] = false;
                diagonal_pos[i - j] = false;
                diagonal_neg[i + j] = false;
                path.pop_back();
            }
        } 

    }
    
    vector<string> build(vector<pair<int, int>>& path) {
        vector<string> result;
        for (int i = 0, idx = 0; i < n; i++) {
            string tmp = "";
            for (int j = 0; j < n; j++) {
                if (idx < path.size() /*明确边界*/ && i == path[idx].first && j == path[idx].second) {
                    tmp.push_back('Q');  
                    idx++;
                } else {
                    tmp.push_back('.');  
                }
            }
            result.push_back(tmp);
        }

        return result;
    }
};

```
