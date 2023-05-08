Download Link: https://assignmentchef.com/product/solved-solved-project-3-passwords
<br>
Some websites impose certain rules for passwords. Write a method that checks whether a string is a valid password. Suppose the password rules are as follows:

1. A password must have at least eight characters, but no more than 32.2. A password consists of only letters, digits, and special characters.3. At least one letter must be upper case and one letter lower case.4. A password must contain at least two digits.5. A password must contain at least one special character.

We desire to test our method with a program that prompts the user to enter a password and displays Valid Password if the rules are followed or Invalid Password followed by the reason otherwise.

Complete the class, CheckPassword shown below, that contains a static method,checkPassword, that performs all of these tests and returns an error code. A returned value of 0 indicates that the password is valid. Any other number corresponds to one of the 5 tests shown above.

The best way to handle this is break it down into a series of smaller tests. For example, implement a boolean method for each rule. Simply have checkPassword sequentially check each rule. If a rule is not satisfied, then the remaining rules are skipped and a value corresponding to that test is returned. For the purpose of this project, the following method names should be used:

1. hasValidSize2. hasValidCharacters3. hasUpperLowerCase4. hasTwoDigits5. hasSpecialCharacters

Each should take a String as a parameter. Checking each rule seems daunting, but the String and Character classes provide all of the functionality necessary. Consider the following:

1. The length method tells you how many characters are in the string.2. The charAt method can extract a single character which may then be compared.3. If ch is of type char, then the method call Character.isDigit(ch) tells you if it is numeric.4. toUpper and toLower methods return strings in the desired case.5. The equals method compares one string with another. For example, if a string is compared with the uppercase version of itself, e.g., if s.equals(s.toUpper())is true, one can deduce that there are no lowercase letters in the string. The following is the outline for the CheckPassword class:

“`java///////////////////////////////////////////////////////////////////////////////////* Validates content of a password returning a code value ////* @param password ////* @return 0 – password is valid ////* 1 – wrong size. ////* 2 – does not consist of only letters, digits, and special characters ////* 3 – does not contain at least one upper case and one lower case character ////* 4 – does not contain at least two digits an invalid character ////* 5 – does not contain any of @, #, $, or % ///////////////////////////////////////////////////////////////////////////////////

public class CheckPassword{

public static int checkPassword(String password){

}

public static int checkPassword(String password){if (hasValidSize(password) == false)return 1;// Add calls to other methods herereturn 0;}

public static boolean hasValidSize(String password){int numberOfCharacters = password.length();if (numberOfCharacters 32 || numberOfCharacters &lt; 8)return false;return true;}// Other methods go here}“`

The following can be used to test the CheckPassword class. Modify it to display the appropriate error message.

“`javapublic class PasswordTester{public static void main(String[] args){String[] passwords ={“abcd”, // Wrong size“abcd_defg”, // Has a non-recognized special character“abcdefgh”, // All one case“Abcdefgh1”, // Needs a second digit“Abcdefgh12”, // Missing a special character“Abcdefgh%12”}; // Validfor (int i=0; i &lt; passwords.length; i++){int code = CheckPassword.checkPassword(passwords[i]);display(code);}}public static void display(int code){System.out.println(code);}}“`