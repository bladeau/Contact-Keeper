# Contact-Keeper
https://reactjs.org/docs/hooks-faq.html#how-to-avoid-passing-callbacks-down

How to avoid passing callbacks down?
We’ve found that most people don’t enjoy manually passing callbacks through every level of a component tree. Even though it is more explicit, it can feel like a lot of “plumbing”.

In large component trees, an alternative we recommend is to pass down a dispatch function from useReducer via context:

Any child in the tree inside app can use the dispatch function to pass actions up:

This is both more convenient from the maintenance perspective (no need to keep forwarding callbacks), and avoids the callback problem altogether. Passing dispatch down like this is the recommended pattern for deep updates.

Note that you can still choose whether to pass the application state down as props (more explicit) or as context (more convenient for very deep updates). If you use context to pass down the state too, use two different context types — the dispatch context never changes, so components that read it don’t need to rerender unless they also need the application state.

