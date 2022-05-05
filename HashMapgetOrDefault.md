# Java HashMap getOrDefault() 方法

getOrDefault() 方法获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值。

getOrDefault() 方法的语法为：

```java
hashmap.getOrDefault(Object key, V defaultValue)
```

**参数说明：**

- key - 键
- defaultValue - 当指定的key并不存在映射关系中，则返回的该默认值

### 返回值

返回 key 相映射的的 value，如果给定的 key 在映射关系中找不到，则返回指定的默认值。

### 题目：

给你一个下标从 0 开始的整数数组 tasks ，其中 tasks[i] 表示任务的难度级别。在每一轮中，你可以完成 2 个或者 3 个 相同难度级别 的任务。

返回完成所有任务需要的 最少 轮数，如果无法完成所有任务，返回 -1 。

 

示例 1：

输入：tasks = [2,2,3,3,2,4,4,4,4,4]
输出：4
解释：要想完成所有任务，一个可能的计划是：
- 第一轮，完成难度级别为 2 的 3 个任务。 
- 第二轮，完成难度级别为 3 的 2 个任务。 
- 第三轮，完成难度级别为 4 的 3 个任务。 
- 第四轮，完成难度级别为 4 的 2 个任务。 
可以证明，无法在少于 4 轮的情况下完成所有任务，所以答案为 4 。
示例 2：

输入：tasks = [2,3,3]
输出：-1
解释：难度级别为 2 的任务只有 1 个，但每一轮执行中，只能选择完成 2 个或者 3 个相同难度级别的任务。因此，无法完成所有任务，答案为 -1 。


提示：

1 <= tasks.length <= 105
1 <= tasks[i] <= 109

```java
class Solution {
	public int minimumRounds(int[] tasks) {
		Map<Integer, Integer> hash = new HashMap<>();
		int len = tasks.length;
		for (int i = 0; i < len; i++) {
			int cur = tasks[i];
			hash.put(cur, hash.getOrDefault(cur, 0) + 1);
		}
		int ans = 0;
		for (Integer entry : hash.values()) {
			if (entry == 1) {
				return -1;
			}
			int mod = entry % 3;
			if (mod == 1) {
				entry = entry - 4;
				ans += 2;
			} else if (mod == 2) {
				entry = entry - 2;
				ans += 1;
			}
			ans += entry / 3;
		}
		return ans;
	}

}
```

