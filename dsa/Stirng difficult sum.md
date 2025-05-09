class Solution {
    public int myAtoi(String s) {
        if (s == null || s.isEmpty()) return 0;

        s = s.trim();
        if (s.isEmpty()) return 0;

        int i = 0, sign = 1;
        long result = 0;

        // Handle sign
        if (s.charAt(i) == '+' || s.charAt(i) == '-') {
            sign = (s.charAt(i) == '-') ? -1 : 1;
            i++;
        }

        // Parse digits
        while (i < s.length() && Character.isDigit(s.charAt(i))) {
            result = result * 10 + (s.charAt(i) - '0');

            // Clamp if out of range
            if (result * sign <= Integer.MIN_VALUE) return Integer.MIN_VALUE;
            if (result * sign >= Integer.MAX_VALUE) return Integer.MAX_VALUE;

            i++;
        }

        return (int) result * sign;
    }
}


look a the result section in whuile loop, thats important.

To check if a charachter is digit or not, charach.isDigit(char)
to change charachter to integer:
**result = result * 10 + (s.charAt(i)-'0');**


