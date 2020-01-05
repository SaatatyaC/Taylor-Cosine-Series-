# Taylor-Cosine-Series-
## ENGR 132 

 Program Description This program will manually calculate the taylor series
 of cos(x). It will go until the nth value is less than the tolerance the
 user gives. The x value is also given by the user. The program will
 return the number of terms it took to reach the tolerance, the computed
 value, and the absolute difference of the computed value and the actual
 value.
```
function[number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_chakra23_fsalek( x_value, tolerance)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% ENGR 132 
% Program Description This program will manually calculate the taylor series
% of cos(x). It will go until the nth value is less than the tolerance the
% user gives. The x value is also given by the user. The program will
% return the number of terms it took to reach the tolerance, the computed
% value, and the absolute difference of the computed value and the actual
% value.
%
% Function Call
%[number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_chakra23_fsalek( x_value, tolerance)

% Input Arguments
% tolerance
% x_value

% Output Arguments
% number_of_terms
% computed_val
% abs_diff
%
% Assignment Information
%   Assignment:  	    PS 08, Problem 2
%   Author:             Frank Salek, fsalek@purdue.edu
%   Team ID:            004-10
%   Paired Programmer:  Saatatya Chakraborty, chakra23@purdue.edu
%   Contributor:        N/A
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```

```
%% ____________________
%% INITIALIZATION
errored = 0; % this will be the variable used to check if theres an error in the input or not
if ~isscalar(x_value) % This will check to see if the x_value input is scalar or not
    errored = 1; % sets the errored to 1 if theres an error
    fprintf('Please enter a scalar value for tolerance')
end
if tolerance >= 1 | tolerance <= 0 %Checks to see if the user input tolerance is within the range
    fprintf('Please enter a tolerance between 0 and 1, not inclusive')
    errored = 1;
end
if errored %if theres an error it will set all the outputs to -99
     number_of_terms = -99;
     computed_val = -99;
     abs_diff = -99;
end
if ~errored % if theres no error it will set everything up
     k_value = 0; %seets the K value to 0
     computed_val = ((((-1) ^ k_value) * (x_value ^ (2 * k_value))) / factorial(2* k_value)); % computed the first nth term
     actual_val = cos(x_value); %finds the actual value
     calc_val = computed_val; % sets the calculated or nth term value as the computed value
     counter = 1; %sets the number of terms to 1
end


%% ____________________
%% CALCULATIONS
% if theres no error it will go through the loop
while ( calc_val > tolerance & ~errored) %goes through the loop until the calculated value is less than the tolerance
    k_value = k_value + 1; %adds one to the k value
    calc_val = ((((-1) ^ k_value) * (x_value ^ (2 * k_value))) / factorial(2 * k_value)); % computes the nth term
    computed_val = computed_val + calc_val; % adds the nth term to the total value
    calc_val = abs(calc_val); %finds the abs value
    counter = counter + 1; %adds one to the counter
end
number_of_terms = counter; %sets the number of terms to the variable
abs_diff = abs(computed_val - actual_val); %computes the abs difference
```

## COMMAND WINDOW OUTPUT
```
% [number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_fsalek_chakra23(.5,.05)
% 
% number_of_terms =
% 
%      3
% 
% 
% computed_val =
% 
%     0.8776
% 
% 
% abs_diff =
% 
%    2.1605e-05

% [number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_fsalek_chakra23(2,.01)
% 
% number_of_terms =
% 
%      5
% 
% 
% computed_val =
% 
%    -0.4159
% 
% 
% abs_diff =
% 
%    2.7382e-04

% [number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_fsalek_chakra23([2,1],.01)
% Please enter a scalar value for tolerance
% number_of_terms =
% 
%    -99
% 
% 
% computed_val =
% 
%    -99
% 
% 
% abs_diff =
% 
%    -99

% [number_of_terms,computed_val,abs_diff] = PS08_taylor_cos_fsalek_chakra23(2,2)
% Please enter a tolerance between 0 and 1, not inclusive
% number_of_terms =
% 
%    -99
% 
% 
% computed_val =
% 
%    -99
% 
% 
% abs_diff =
% 
%    -99
```
