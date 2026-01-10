# 🚀 Progress Tracker

A static website for tracking DSA (Data Structures and Algorithms) problems and learning topics. The site is hosted on Vercel at [https://progresstracker1.vercel.app/](https://progresstracker1.vercel.app/)

## 📁 Project Structure

```
progress_tracker/
├── index.html                    # Landing page
├── detail.json                   # Central data file tracking all entries
├── maitry_dsa.html              # Maitry's DSA problems listing page
├── maitry_learn.html            # Maitry's learning topics listing page
├── khushie_dsa.html             # Khushie's DSA problems listing page
├── khushie_learn.html           # Khushie's learning topics listing page
├── styles/                       # CSS stylesheets
│   ├── style.css                # Landing page styles
│   ├── dsa.css                  # DSA listing pages styles
│   └── learn.css                # Learning topics listing pages styles
└── people/                       # Individual progress entries
    ├── maitry/
    │   ├── dsa/                 # Maitry's DSA problem solutions
    │   │   ├── contains_duplicate.html
    │   │   └── dsa_style.css
    │   └── learn/               # Maitry's learning topic notes
    │       ├── network_layers.html
    │       └── learn_style.css
    └── khushie/
        ├── dsa/                 # Khushie's DSA problem solutions
        │   ├── contains_duplicate.html
        │   └── dsa_style.css
        └── learn/               # Khushie's learning topic notes
            ├── network_layers.html
            └── learn_style.css
```

## 🔧 How It Works

### Landing Page (`index.html`)
The landing page provides navigation to:
- DSA Problems section for each person
- Learning Topics section for each person

### Listing Pages
Each person has two listing pages:
- `{person}_dsa.html` - Displays all DSA problems solved by that person
- `{person}_learn.html` - Displays all learning topics studied by that person

These pages **dynamically load entries** from `detail.json` and display them as cards with:
- Problem/Topic title
- Link to the detailed page
- Date when it was added

### Individual Progress Pages
Each entry has its own HTML page located at:
- `people/{person_name}/dsa/{filename}.html` for DSA problems
- `people/{person_name}/learn/{filename}.html` for learning topics

These pages contain the detailed content (problem solutions, explanations, code, etc.).

### Central Data File (`detail.json`)
The `detail.json` file serves as the central registry for all progress entries. It has the following structure:

```json
{
  "people": {
    "person_name": {
      "dsa": [
        {
          "title": "Problem Title",
          "file": "filename.html",
          "date": "YYYY-MM-DD"
        }
      ],
      "learn": [
        {
          "title": "Topic Title",
          "file": "filename.html",
          "date": "YYYY-MM-DD"
        }
      ]
    }
  }
}
```

## ➕ How to Add New Progress

To add a new progress entry, follow these steps:

### Step 1: Create the HTML File
Create a new HTML file in the appropriate folder:
- For DSA: `people/{person_name}/dsa/{your_filename}.html`
- For Learning: `people/{person_name}/learn/{your_filename}.html`

**Example:** To add a new DSA problem for Maitry:
- Create: `people/maitry/dsa/two_sum.html`

### Step 2: Add Entry to `detail.json`
Add a new entry to the corresponding array in `detail.json`:

```json
{
  "people": {
    "maitry": {
      "dsa": [
        {
          "title": "Contains Duplicate",
          "file": "contains_duplicate.html",
          "date": "2026-01-10"
        },
        {
          "title": "Two Sum",           // ← New entry
          "file": "two_sum.html",        // ← Matches filename from Step 1
          "date": "2026-01-11"          // ← Date in YYYY-MM-DD format
        }
      ],
      "learn": [...]
    }
  }
}
```

### Step 3: Ensure File Paths Are Correct
The listing pages generate links based on the `file` field in `detail.json`. Make sure:
- The `file` field matches the actual filename you created
- The path structure follows: `people/{person_name}/{dsa|learn}/{file}`

## 📝 File Templates

### DSA Problem Template
For DSA problems, create an HTML file with:
- Problem statement
- Multiple approaches with time/space complexity
- Code implementations in various languages (using Prism.js for syntax highlighting)
- Key insights

Reference: `people/maitry/dsa/contains_duplicate.html`

### Learning Topic Template
For learning topics, create an HTML file with:
- Brief description
- 1-minute explanation
- 5-minute explanation
- 10-minute deep dive
- Important points to remember

Reference: `people/maitry/learn/network_layers.html`

## 🎨 Styling

The project uses separate CSS files:
- `styles/style.css` - Landing page
- `styles/dsa.css` - DSA listing pages
- `people/{person}/{dsa|learn}/{dsa|learn}_style.css` - Individual entry pages

Each person's folder can have its own styling files for the detail pages.

## 🔗 Navigation Flow

1. **Landing Page** (`index.html`)
   ↓
2. **Person's Listing Page** (`{person}_{dsa|learn}.html`)
   ↓
3. **Individual Entry Page** (`people/{person}/{dsa|learn}/{file}.html`)

Each page has a "Back" button to navigate to the previous level.

## 🚀 Deployment

This is a static website that can be deployed on:
- Vercel (currently deployed)
- GitHub Pages
- Netlify
- Any static hosting service

Simply upload all files and the site will work! The JavaScript in the listing pages fetches `detail.json` dynamically, so make sure it's accessible.

## 📌 Important Notes

1. **File Naming**: Use lowercase with underscores for filenames (e.g., `two_sum.html`, `binary_search.html`)
2. **Date Format**: Always use `YYYY-MM-DD` format in `detail.json`
3. **JSON Structure**: Maintain the exact JSON structure in `detail.json` - the listing pages depend on it
4. **File Paths**: The `file` field in `detail.json` should only contain the filename, not the full path
5. **Order**: Entries in the arrays are displayed in the order they appear in `detail.json`

## 🛠️ Adding a New Person

To add a new person to track:

1. Add their entry to `detail.json`:
```json
{
  "people": {
    "newperson": {
      "dsa": [],
      "learn": []
    }
  }
}
```

2. Create their folder structure:
```
people/
  └── newperson/
      ├── dsa/
      └── learn/
```

3. Create listing pages: `newperson_dsa.html` and `newperson_learn.html` (copy from existing person's pages and update the person name)

4. Update `index.html` to add links to the new person's pages

## 📚 Example Workflow

Let's say Maitry wants to add a new DSA problem "Reverse Linked List":

1. Create `people/maitry/dsa/reverse_linked_list.html` with the problem solution
2. Add to `detail.json`:
```json
"dsa": [
  {
    "title": "Reverse Linked List",
    "file": "reverse_linked_list.html",
    "date": "2026-01-12"
  }
]
```
3. The entry will automatically appear on `maitry_dsa.html` listing page!

---

Happy tracking! 🎉

