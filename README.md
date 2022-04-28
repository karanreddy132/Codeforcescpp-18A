# Codeforcescpp-18A
#include <bits/stdc++.h>

using namespace std;

bool is_right(int x1, int y1, int x2, int y2, int x3, int y3) {
	if ((x1 == x2 && y1 == y2) || (x2 == x3 && y2 == y3) ||
		(x1 == x3 && y1 == y3)) {
		return false;
	}
	if (((y1 - y2) * (y2 - y3) + (x1 - x2) * (x2 - x3)) == 0 ||
		((y2 - y3) * (y3 - y1) + (x2 - x3) * (x3 - x1)) == 0 ||
		((y3 - y1) * (y1 - y2) + (x3 - x1) * (x1 - x2)) == 0) {
		return true;
	}
	return false;
}

int main() {
	int points[7];
	for (int i = 0; i < 6; i++) {
		cin >> points[i];
	}
	if (is_right(
			points[0], points[1], points[2], points[3], points[4], points[5])) {
		cout << "RIGHT";
		return 0;
	}
	for (int i = 0; i < 6; i++) {
		points[i]++;
		if (is_right(
				points[0],
				points[1],
				points[2],
				points[3],
				points[4],
				points[5])) {
			cout << "ALMOST";
			return 0;
		}
		points[i] -= 2;
		if (is_right(
				points[0],
				points[1],
				points[2],
				points[3],
				points[4],
				points[5])) {
			cout << "ALMOST";
			return 0;
		}
    points[i]++;
	}
	cout << "NEITHER";
	return 0;
}
