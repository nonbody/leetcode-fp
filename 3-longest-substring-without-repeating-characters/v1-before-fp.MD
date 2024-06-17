```ts
// leetcode provided func type
function lengthOfLongestSubstring(s: string): number {
    const n = s.length;
    let max = 0;
    const arr: string[] = [];

    const shiftFunc = (target: string) => {
        const v = arr.shift();
        if (v !== target) {
            shiftFunc(target);
        }
    };

    for (let i = 0; i < n; i++) {
        const first = s.charAt(0);
        if (arr.includes(first)) {
            max = arr.length > max ? arr.length : max;
            shiftFunc(first);
        }
        arr.push(first);
        s = s.substring(1);
    }
    max = arr.length > max ? arr.length : max;
    return max;
};
```
