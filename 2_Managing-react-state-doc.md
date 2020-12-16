# Managing React State

## What is State?

- App data that may change over time.

## Eight Ways to Handle State in React App.

In React app there are at least Eight different ways to handle Sate.

1. URL ( Current app location / settings )

   - Store state in url, this is usefull for tracking where the user is in the App as well as their current settings.
     Example of location related information should be stored inside the url: - Current item ( being viewed ) - Filters - Pagination - Sorting
   - Supports deep linking
     - keeping location related data in url means that users can share deep links with others.
     
    - Avoid redundantly storing in your app
        - To avoid the url in your app getting out of sync, its usefull to avoid storing such location information in your app state
        - Use the url is the system of record, read form it as needed for such information and update the url as needed when such settings changed.
    - Consider **React Router**
        - react-router is not a part of react, but its a popular third party library that help with above concerns. **We can use react-router to handle URL related state**.


2. Web storage
3. Local state
4. Lifted state
5. Derived state
6. Refs
7. Context
8. Third party library
