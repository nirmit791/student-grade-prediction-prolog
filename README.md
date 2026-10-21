
% Student Grade Prediction System
% AICA Mini Project

% Calculate the overall score
calculate_score(Marks, Attendance, Hours, Score) :-
    StudyScore is min(Hours * 10, 100),
    Score is Marks * 0.6
           + Attendance * 0.2
           + StudyScore * 0.2.

% Grade prediction rules
predict_grade(Score, a) :- Score >= 80, !.
predict_grade(Score, b) :- Score >= 70, !.
predict_grade(Score, c) :- Score >= 60, !.
predict_grade(Score, d) :- Score >= 40, !.
predict_grade(_, f).

% Feedback rules
feedback(a, 'Excellent performance!').
feedback(b, 'Very good performance!').
feedback(c, 'Good. Keep improving!').
feedback(d, 'More practice needed.').
feedback(f, 'Needs improvement.').

% Example prediction
main :-
    Marks = 80,
    Attendance = 90,
    Hours = 6,
    calculate_score(Marks, Attendance, Hours, Score),
    predict_grade(Score, Grade),
    feedback(Grade, Message),
    format('Overall Score: ~2f/100~n', [Score]),
    format('Predicted Grade: ~w~n', [Grade]),
    format('Feedback: ~w~n', [Message]).
