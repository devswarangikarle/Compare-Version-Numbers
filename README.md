# Compare-Version-Numbers

Given two version strings, version1 and version2, compare them. A version string consists of revisions separated by dots '.'. The value of the revision is its integer conversion ignoring leading zeros.
To compare version strings, compare their revision values in left-to-right order. If one of the version strings has fewer revisions, treat the missing revision values as 0.
Return the following:
If version1 < version2, return -1.
If version1 > version2, return 1.
Otherwise, return 0.

Constraints:

1 <= version1.length, version2.length <= 500
version1 and version2 only contain digits and '.'.
version1 and version2 are valid version numbers.
All the given revisions in version1 and version2 can be stored in a 32-bit integer.

class Solution:

    def compareVersion(self, version1: str, version2: str) -> int:
        def helper(s: str, idx: int) -> List[int]:
            num = 0
            while idx < len(s):
                if s[idx] == '.':
                    break
                else:
                    num = num * 10 + int(s[idx])
                idx += 1
            return [num, idx+1]

        i = j = 0
        while(i < len(version1) or j < len(version2)):
            v1, i = helper(version1, i)
            v2, j = helper(version2, j)
            if v1 > v2:
                return 1
            elif v1 < v2:
                return -1

        return 0
