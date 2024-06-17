```ts
const shiftFunc = (target: string, arr: string[]) => {
  const v = arr.shift();
  if (v !== target) {
    shiftFunc(target, arr);
  }
};

// main
function lengthOfLongestSubstring(s: string): number {
  let max = 0;
  const longest: string[] = [];

  for (let i = 0; i < s.length; i++) {
    const first = s.charAt(i);
    if (longest.includes(first)) {
      max = Math.max(longest.length, max);
      shiftFunc(first, longest);
    }
    longest.push(first);
  }
  return Math.max(longest.length, max);
}
```
