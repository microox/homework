# Homework Assignment 03 -- Software Design & Programming Techniques (WS 2016)
You have one week to work on your handin. The deadline for this assignment is
Nov 13th, 23:59.

Work in the same groups as in the last exercise. Please
provide all members names in your handin. This exercise builds
up on the last exercise. So please continue working in the
same github repository. Open a new issue to hand in your solution of this
assignment. In this issue, also include brief textual explanations
of what you changed and provide short reasoning for these changes.

## Task 1. Designing a Library for Surveys (Part II)

We build on your results of the first iteration from [homework assignment 02](/hw02/README.md).
Modify your design and implementation to also account for the following new
user stories.

### User Stories

#### Story #5

      ------------------------------------------------------------------------
      As a survey developer I want to describe multiple choice
      questions to restrict the answer possibilities to given choices.

        Description: Using the survey library API, I want to create multiple
          choice questions with a fixed set of possible answers the user can
          choose from. I want to be able to reuse answer options that often
          occur, such as a Likert scale for agreement:

            "Strongly Agree / Agree / Undecided / Disagree / Strongly Disagree"

          or for frequency:

            "Very Frequently / Frequently / Occasionally / Rarely / Never"

        Acceptance Criteria:
          - users can only select one of the possible answers
          - answer options can freely be reused
          - answer options for multiple choice questions are printed as
            "( ) Strongly Agree" on a single line, indented by two spaces.
          - in the report, the text of the selected answer options is reported
            as answer for the question.
      ------------------------------------------------------------------------


#### Story #6

      ------------------------------------------------------------------------
      As a survey developer I want to describe yes/no questions with
      a fixed binary answer scheme.

        Description: Using the survey library API, I want to create yes/no
          questions. The answer text of the yes/no questions can vary. Most
          of the time it is "yes/no", but sometimes also "agree/disagree" or
          other text.

        Acceptance Criteria:
          - users can only select one of the possible answers
          - both answer options for yes/no questions are printed as
            "( ) yes,  ( ) no" on a single line, indented by two spaces.
          - in the report, the text of the selected answer options is reported
            as answer for the question.
      ------------------------------------------------------------------------

#### Story #7
      ------------------------------------------------------------------------
      As a survey developer I want to be able to mark questions as
      "mandatory" to require the user to fill in this question.

        Description:
          Sometimes it is necessary to assert, that the user gives an
          answer to a question. This should be possible for all kinds
          of questions.

        Acceptance Criteria:
          - questions can be marked as mandatory after they have been
            defined.
          - the mandatory marking can be removed from a question to be
            reused in some other survey where it is not mandatory.
          - A printed mandatory question should include a textual explanation
            like "This question is mandatory".
          - The survey runtime system should assert that mandatory questions are
            actually filled. For freetext questions that is, the answer should
            be at least two (2) non-space characters. For multiple choice and
            yes/no questions one of the answer options should be selected.
      ------------------------------------------------------------------------

#### Story #8
      ------------------------------------------------------------------------
      As a survey developer I want to be able to mark questions as
      dependent on another yes/no question to model flow charts for my
      customers.

        Description:
          Given two questions A and B where A is a yes/no question, I want
          to mark question B as dependent on the result of question A.
          In that case, B is only relevant if A has been positively answered.

        Acceptance Criteria:
          - in interaction mode, the user is only asked question B when
            question A has been answered with "yes" (or another positive answer).
          - in printed form the question B is annotated with the dependency
            to question A ("please only fill this question if you answered
            question A with 'yes'")
          - question A occurs (both in print and in interaction mode) before
            question B.
          - validation checks that question A and question B are contained in
            one survey, so that the reference makes sense.
          - validation checks that question A is mandatory.
          - (optional) validation checks that there is no (transitive)
            dependency from question A to question B. That is, there are no
            dependency cycles.
      ------------------------------------------------------------------------

Describe briefly how your design decisions from the last exercise
influenced the implementation of the new requirements:

- Which of these requirements could be implemented without changing existing code?
  (just adding new code in some additional module / class / method)

- Which of these requirements could be implemented by only locally changing code?
  (inside one module / class / method)

- Which of these requirements required (global / systematic) changes of your design?

## Task 2. The Open Closed Principle (OCP)
Briefly answer the following questions:

1. What is the Open Closed Principle (OCP)?

2. Why is abstraction the key to the OCP? Which kinds of abstractions exist in
  your favorite OO programming language. Which kinds of abstractions exist in
  your favorite FP programming language.

3. Explain why your design of the survey library might violate the OCP. What
   extensions can be expected in the future?

4. Give examples of future extensions that are well supported by your design.
