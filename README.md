# A/B Testing

## Introduction

**Project Description**

Our task is to evaluate the results of an A/B test. We have a dataset containing user actions, a technical specification, and several auxiliary datasets. Our objectives are:

1. Assess the correctness of the test implementation.
2. Analyze the test results.

To evaluate the correctness of the test implementation, we will check the following:

1. Intersection of the test audience with a competing test.
2. Alignment of the test with marketing events and other issues regarding the temporal boundaries of the test.

**Technical Specification**

1. Test name: `recommender_system_test`.
2. Groups: A - control group, B - new payment funnel.
3. Launch date: December 7, 2020.
4. Date to stop collecting new users: December 21, 2020.
5. End date: January 4, 2021.
6. Audience: 15% of new users from the EU region.
7. Test objective: testing changes related to the implementation of an improved recommender system.
8. Expected number of test participants: 6000.
9. Expected effect: within 14 days from registration, users should show an improvement of at least 10% for each metric: conversion to product page views (event: product_page), views of the product cart (event: product_cart), and purchases (event: purchase).

**Data Description**

`ab_project_marketing_events.csv` - calendar of marketing events for the year 2020.

File structure:
1. `name` - name of the marketing event.
2. `regions` - regions where the advertising campaign will take place.
3. `start_dt` - start date of the campaign.
4. `finish_dt` - end date of the campaign.

`final_ab_new_users.csv` - users who registered from December 7 to December 21, 2020.

File structure:
1. `user_id` - user identifier.
2. `first_date` - registration date.
3. `region` - user's region.
4. `device` - device used for registration.

`final_ab_events.csv` - actions of new users from December 7, 2020, to January 4, 2021.

File structure:
1. `user_id` - user identifier.
2. `event_dt` - date and time of the event.
3. `event_name` - type of event.
4. `details` - additional data about the event. For purchases (event: purchase), this field contains the cost of the purchase in dollars.

`final_ab_participants.csv` - table of test participants.

File structure:
1. `user_id` - user identifier.
2. `ab_test` - test name.
3. `group` - user group.

**Work Plan**

1. Data exploration: type conversion, identification of missing values and duplicates.
2. Assess the correctness of the test implementation. Check the following:
   1. Data compliance with the technical specification. Correctness of all technical specification points.
   2. Test timing: it should not coincide with marketing or other activities.
   3. Test audience: ensure there are no overlaps with a competing test and no users participating in both test groups simultaneously. Check the uniform distribution across test groups and the correctness of their formation.
3. Perform exploratory data analysis:
   1. Are the number of events per user evenly distributed in the samples?
   2. How is the number of events distributed over the days in the samples?
   3. How does the conversion in the funnel change at different stages in the samples?
   4. What data peculiarities should be considered before starting A/B testing?
4. Evaluate the results of A/B testing:
   1. What can be said about the results of A/B testing?
   2. Check the statistical difference in proportions using the z-test.
5. Make a general conclusion about the correctness of the test implementation.
