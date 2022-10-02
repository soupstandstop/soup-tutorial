Neetcode.io
===========

[週報]2022/9/29~2022/10/02
--------------------------
找到了Neetcode.io網站，可以依照Topic分類題目，像是Arrays, Two pointers, Sliding Window,...，每個Topic分別有2題左右easy, medium, Hard，總共150題，循環做每個Topic的easy, 再循環做每個Topic的medium

Two pointers的125. Valid Palindrome:
思路：
先移除字串內所有非字母和數字符號: 
想到可以用ASCII轉換去找範圍，如果範圍不在A~Z or a~z or 0~9裡面，則刪除，可使用ord()
也可以使用re正則表達式去清，與Shell script處理字串應該是一樣語法: [^A-Za-z0-9]將非這三組範圍的給移除
從左到右要跟從右到左一樣:
想到可以放兩個指標，一個i一個j，i放在最左邊，j放在最右邊，每次循環i+1, j-1，接著判斷該index的str是否相同，不相同即可直接結束回傳False
如果都一樣，循環至i>=j之前可結束
一樣的話回傳True，不一樣回傳False

Sliding window的121. Best Time to Buy and Sell Stock:
思路：

第一個結果188/211 test cases fail
先想到將price做sorted排序
Python的sort & sorted不同，sort會將原本的list直接更動，sorted不會更動原本list，可以另assign新list專門存放排序後結果(list.sort() vs sorted(list))
並將原本prices_list的price2index存成dict
將排序後的最大值減去最小值得到max_window
並且循環將min_window找出
While loop min_window <= max_window, max_window -= 1
去比對此window有無符合低價在左，高價在右，並且使用第2點的dict去mapping index
結果失敗，因為股價會有重複的情況，所以會在第2點時錯誤

第二個結果Time Limit Error
想到for loop將每一天的股價相減存起來，找出max diff price即可，但時間複雜度太高失敗了

第三個找了一下別人解法，還是沒有很懂，現在看github有人用動態規劃內的狀態轉移方程解決Leetcode股價買賣系列問題(https://github.com/labuladong/fucking-algorithm/blob/5645c911dd42ed6cf285bcf16077b72c64c8ed08/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%E7%B3%BB%E5%88%97/%E5%9B%A2%E7%81%AD%E8%82%A1%E7%A5%A8%E9%97%AE%E9%A2%98.md)，看了以下兩篇正在研究中，還沒看完，複習遞迴跟動態規劃
DP: https://www.cxyxiaowu.com/8536.html
Recursive: https://mp.weixin.qq.com/s?__biz=MzI5MTU1MzM3MQ==&mid=2247483813&idx=1&sn=423c8804cd708b8892763a41cfcc8886&scene=21#wechat_redirect

[週報]2022/10/03~2022/10/09
----------------------------