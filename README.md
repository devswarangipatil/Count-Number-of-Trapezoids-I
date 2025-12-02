# Count-Number-of-Trapezoids-I

You are given a 2D integer array points, where points[i] = [xi, yi] represents the coordinates of the ith point on the Cartesian plane.

A horizontal trapezoid is a convex quadrilateral with at least one pair of horizontal sides (i.e. parallel to the x-axis). Two lines are parallel if and only if they have the same slope.

Return the number of unique horizontal trapezoids that can be formed by choosing any four distinct points from points.

Since the answer may be very large, return it modulo 10^9 + 7.

class Solution:

    def countTrapezoids(self, points: List[List[int]]) -> int:
        MOD = (10 ** 9) + 7
        res = 0
        d = Counter(y for _,y in points)
        y_points = tuple(v * (v-1) // 2 for v in d.values())
        s = sum(y_points)
        for y in y_points:
            s -= y
            res += y * s
        return res % MOD

