# Python-Programming-Week-9
1.Uncommon words

A sentence is a string of single-space separated words where each word consists only of lowercase letters.A word is uncommon if it appears exactly once in one of the sentences, and does not appear in the other sentence.

Given two sentences s1 and s2, return a list of all the uncommon words. You may return the answer in any order.

CODE:

def uncommon_words(s1, s2):

    word_count = {}

    for word in s1.split():

        word_count[word] = word_count.get(word, 0) + 1

    for word in s2.split():

        word_count[word] = word_count.get(word, 0) + 1

    uncommon_words = [word for word, count in word_count.items() if count == 1]

    return ' '.join(uncommon_words)



s1 = input().strip()

s2 = input().strip()



print(uncommon_words(s1, s2))

#2.Sort Dictionary by Values Summation

Give a dictionary with value lists, sort the keys by summation of values in value list.

 

CODE:

def sort_dict_by_value_sum(test_dict):

    sorted_dict = {}

    sorted_keys = sorted(test_dict, key=lambda x: sum(test_dict[x]))

    for key in sorted_keys:

        sorted_dict[key] = sum(test_dict[key])

    return sorted_dict



n = int(input().strip())



input_dicts = {}



for _ in range(n):

    data = input().split()

    key = data[0]

    values = list(map(int, data[1:]))

    input_dicts[key] = values



sorted_dicts = sort_dict_by_value_sum(input_dicts)



for key, value in sorted_dicts.items():

    print(key, value)
#3.Winner of Election

Given an array of names of candidates in an election. A candidate name in the array represents a vote cast to the candidate. Print the name of candidates received Max vote. If there is tie, print a lexicographically smaller name.



CODE:

def find_winner(votes):

    vote_count = {}

    for candidate in votes:

        if candidate in vote_count:

            vote_count[candidate] += 1

        else:

            vote_count[candidate] = 1

    max_votes = max(vote_count.values())

    winners = [candidate for candidate, votes in vote_count.items() if votes == max_votes]

    return min(winners)



n = int(input().strip())

votes = [input().strip() for _ in range(n)]

print(find_winner(votes))
#4.Student Record



Create a student dictionary  for n students with the student name as key and their test mark assignment mark and lab mark as values. Do the following computations and display the result.

1.Identify the student with the  highest average score

2.Identify the student who as the highest Assignment marks

3.Identify the student with the Lowest lab marks

4.Identify the student with the lowest average score

Note:

If more than one student has the same score display all the student names



CODE:

def main():

    import sys

    input = sys.stdin.read

    data = input().strip().split('\n')

    

    n = int(data[0].strip())

    s = {}

    

    for i in range(1, n + 1):

        l = data[i].strip().split()

        name = l[0]

        t = int(l[1])

        a = int(l[2])

        lab = int(l[3])

        s[name] = (t, a, lab)

    

    high_avg = -1

    high_assign = -1

    low_lab = float('inf')

    low_avg = float('inf')

    

    high_avg_students = []

    high_assign_students = []

    low_lab_students = []

    low_avg_students = []

    

    for name, (t, a, lab) in s.items():

        avg = (t + a + lab) / 3

        

        if avg > high_avg:

            high_avg = avg

            high_avg_students = [name]

        elif avg == high_avg:

            high_avg_students.append(name)

        

        if a > high_assign:

            high_assign = a

            high_assign_students = [name]

        elif a == high_assign:

            high_assign_students.append(name)

        

        if lab < low_lab:

            low_lab = lab

            low_lab_students = [name]

        elif lab == low_lab:

            low_lab_students.append(name)

        

        if avg < low_avg:

            low_avg = avg

            low_avg_students = [name]

        elif avg == low_avg:

            low_avg_students.append(name)

    

    high_avg_students.sort()

    high_assign_students.sort()

    low_lab_students.sort()

    low_avg_students.sort()

    

    print(" ".join(high_avg_students))

    print(" ".join(high_assign_students))

    print(" ".join(low_lab_students))

    print(" ".join(low_avg_students))

main()
#5.Scramble Score



In the game of Scrabble™, each letter has points associated with it. The total score of a word is the sum of the scores of its letters. More common letters are worth fewer points while less common letters are worth more points. 

Write a program that computes and displays the Scrabble™ score for a word. Create a dictionary that maps from letters to point values. Then use the dictionary to compute the score.

A Scrabble™ board includes some squares that multiply the value of a letter or the value of an entire word. We will ignore these squares in this exercise.

CODE:

def scrabble_score(word):

    letter_values = {

        'A': 1, 'E': 1, 'I': 1, 'L': 1, 'N': 1, 'O': 1, 'R': 1, 'S': 1, 'T': 1, 'U': 1,

        'D': 2, 'G': 2,

        'B': 3, 'C': 3, 'M': 3, 'P': 3,

        'F': 4, 'H': 4, 'V': 4, 'W': 4, 'Y': 4,

        'K': 5,

        'J': 8, 'X': 8,

        'Q': 10, 'Z': 10

    }

    

    score = sum(letter_values.get(letter.upper(), 0) for letter in word)

    return f"{word} is worth {score} points."



word = input().strip()

print(scrabble_score(word))




