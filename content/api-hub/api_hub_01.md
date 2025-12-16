---
title: Day 1 – Building the Search Filter and Dynamic Pages
---


My goal today was to finish a basic search filter, set up a temporary layout just to visualize things better, and create dynamic pages for each API using React Router.  
If you're new here, check out my [previous post](./api_hub_00.md), where I explain what I'm building and the stack I'm using.

---

## 📁 Initial Project Structure

I started by creating a `components` folder to hold the `Header`, `Footer`, and `SearchBar`.

My first thought was figuring out how exactly to create some test data to see if I could get the filter working.  
I haven’t built many search bars so far, but my brain already screams:

> **target input value → use state to update → filter with `includes` and `toLowerCase`**

I just needed to connect the dots.

---

## 🧪 Creating Fake Data

The first thing I did was create `testData`: just a few mock values in an array of objects, simulating real API pages.  
I put everything in a single variable to make it easier to manipulate later using the spread operator.

```js
export const testTools = [
    {
      name: "API Image generator",
      route: '/image-generator',
      description: "Generate images for free",
      categories: ['API', 'Image generator']
    },
    {
      name: "PDF Merger",
      route: '/pdf-merger',
      description: "Merge multiple PDF files into one",
      categories: ['PDF', 'File Management']
    },
  ...
]


const allTools = [...testTools]
```

---

## 🧠 Filter Logic and Security

With that in hand, it was time to get to work. I started with `useState` for `searchQuery`, to store what the user types.

If it were plain JavaScript, I'd use an `eventListener` with an arrow function.  
Since we're using React, a function passed to the input’s `onChange` works perfectly.

```js
const [searchQuery, setSearchQuery] = useState('')

const handleSearchChange = (e) => {
  const sanitizeQuery = DOMPurify.sanitize(e.target.value)
  setSearchQuery(sanitizeQuery)
}
```

I’m a bit paranoid about security 😅, so I use DOMPurify to sanitize user input and prevent malicious scripts or commands from being processed or stored.

---

## 🔍 Implementing the Filter

With state working and input sanitized, I moved on to filtering.

I used `.filter()` on `allTools`, converting both `tool.name` and `searchQuery` to lowercase and applying `includes`:

```js
const filteredTools = allTools.filter((tool) =>
  tool.name.toLowerCase().includes(searchQuery.toLowerCase())
)
```

---

## 🧩 Connecting the Components

I passed `searchQuery` and `handleSearchChange` as props to the `SearchBar` component.  
Inside the input, I used `value={searchQuery}` and `onChange={onSearchChange}`, making it controlled and reactive.

```jsx
<SearchBar searchQuery={searchQuery} onSearchChange={handleSearchChange} />
```

---

## 🖼️ Displaying the Results

Finally, I created the `ApiCard` component, a reusable card that takes `title`, `description`, and `btn`.  
I rendered each filtered result using `.map()` and added a simple check: if no results are found, display a friendly message.

```jsx
{filteredTools.length > 0 ? (
  filteredTools.map((tool, index) => (
    <ApiCard
      key={index}
      title={tool.name}
      description={tool.description}
      btn="Access here"
    />
  ))
) : (
  <p className="text-center text-gray-500 mt-4">
    No tools found.
  </p>
)}
```

---


💬 I know this setup is still very basic, and it’s definitely not following all best practices.
But since I’m building it step by step, I’m improving and adjusting things as I go.

Right now, my focus is on getting the structure in place — I’ll polish it later.
What matters is having something closer to done than perfect. 😄

## ✅ Summary so far:

- The search input works in real-time  
- The data is filtered based on the tool name  
- The list updates dynamically  
- The input is sanitized using DOMPurify  
- Everything is modularized into reusable components.
