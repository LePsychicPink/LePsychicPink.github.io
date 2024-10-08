---
title: State Management Tools
date: 2024-09-14 01:27:25
tags: React
categories: Programming
---

The most popular example of state management is Redux

### Altenatives for state management in React

- Zustand
- Flux

### Redux Tool Kit (RTK)

### Zustand

create a `store.ts` in wherever you want

```Typescript
import { create } from "zustand";

interface BearState {
  bears: number;
  increasePopulation: () => void;
  removeAllBears: () => void;
  updateBears: (newBears: number) => void;
}

export const useStore = create<BearState>()((set) => ({
  bears: 0,
  increasePopulation: () => set((state) => ({ bears: state.bears + 1 })), // if you need to access the state
  removeAllBears: () => set({ bears: 0 }), // if you only need to set value
  updateBears: (newBears: number) => set({ bears: newBears }), // if you have input
}));
```
