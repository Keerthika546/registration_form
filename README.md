# Registration Page with Welcome Popup

A responsive registration page that validates user input, then redirects to my [Udemy Clone](https://keerthika546.github.io/udemy-clone/) where a personalised career-focused welcome popup greets the user by name.

**Live Udemy clone:** https://keerthika546.github.io/udemy-clone/

## Features

- Sign up form with Name, E-mail, Password and Confirm Password
- Icons inside each input (Font Awesome) that change colour on focus
- Custom validation messages (required, minimum length, email format, passwords must match)
- Sign up button stays disabled until the whole form is valid
- Redirects to the Udemy clone after a successful sign up
- Welcome popup on the Udemy page with the user's name
- Fully responsive (works on phones, tablets and desktops)
- Background image layer with a purple overlay, glass-style form and a 3D-style button

## Tech Stack

- HTML5
- Tailwind CSS
- JavaScript (vanilla)
- Font Awesome icons
- GitHub Pages (hosting)

## How It Works

```
Registration page  ->  validate form  ->  redirect with ?welcome=1&name=<name>
                                                    |
                                                    v
                          Udemy clone reads the URL  ->  shows welcome popup
```

1. The user fills in the form. The browser's built-in checks plus custom JavaScript checks run on every keystroke.
2. When all fields are valid, the Sign up button is enabled.
3. On submit, the name is encoded with `encodeURIComponent` and sent in the URL.
4. The Udemy clone page reads the URL with `URLSearchParams`, shows the popup, then cleans the address bar with `history.replaceState` so a refresh does not show it again.

## Run Locally

1. Clone the repository
   ```bash
   git clone https://github.com/Keerthika546/<your-repo-name>.git
   ```
2. Open the registration page in your browser (double-click the file, or use the VS Code Live Server extension).
3. Fill in the form and click **Sign up**.

## What I Learnt

### JavaScript and the DOM
- Reading input values: `.value` for text, email and number inputs, `:checked` for radio buttons, and `select.value` for dropdowns
- Creating elements with `createElement`, adding them with `append`, and showing text safely with `textContent`
- Event listeners, and why the `submit` event is better than `click` for forms
- Stopping page reloads with `event.preventDefault()`
- Closures: how a Delete button remembers the exact row it belongs to
- Optional chaining (`?.`) and the `||` fallback to avoid errors when nothing is selected
- `var` holding an element versus holding a string (calling `.value` too early breaks `addEventListener`)
- Event delegation and `closest()` for finding a parent row

### Form validation
- HTML attributes: `required`, `minlength`, `type="email"`, `pattern`, `title`
- Custom messages with `setCustomValidity` and the `invalid` event
- Why `setCustomValidity("")` must be cleared, or the form can never submit
- Checking password match live on both password fields
- Disabling the submit button with `form.checkValidity()`
- Why `type="email"` alone is loose, and how a `pattern` (regex) tightens it
- Front-end validation is for user convenience; real validation must happen on the server

### HTML and CSS
- `label for` + `input id` (bigger click area and accessibility), and why ids must be unique
- Radio buttons share a `name`; ids and `for` must match exactly
- `position: relative` / `absolute`, `inset-0`, and layering a background image under content
- Centering with Flexbox (`justify-center`, `items-center`) and what `flex-col` changes
- Why `opacity` on a parent also fades its children, so the image needs its own layer
- Placing icons inside inputs and centering them with `inset-y-0 flex items-center`
- `:focus-within` for styling a parent when a child input is focused
- Making a full-screen modal with `fixed inset-0`, and why inline styles beat classes
- Responsive design with breakpoints (`sm:`, `md:`), `clamp()`, and the viewport meta tag

### Tailwind CSS
- Utility-first styling, and mobile-first breakpoints
- Differences between Tailwind v2 (prebuilt stylesheet) and v3 (CDN script): `group-focus-within`, arbitrary values like `shadow-[...]`, and `bg-white/10` do not work in v2
- Preflight resets inputs, which is why inputs look invisible until given a border

### Browser and deployment
- `localStorage` is separate for each origin, so pages on different addresses cannot share it
- Passing data between pages with URL parameters (`URLSearchParams`, `encodeURIComponent`)
- The back/forward cache restores old form values, so the form is reset before redirecting
- Chrome's Password Manager can warn about leaked passwords even in a test project
- Deploying a site with GitHub Pages and finding the live link
- Debugging with the browser Console: `null` errors usually mean a wrong id or a script running before the element exists

## Future Improvements

- Connect the form to a backend (Spring Boot) and store users in a database
- Hash passwords on the server and verify emails by sending a confirmation link
- Add a login page
- Show validation messages under each field instead of the browser's default bubble
- Add a password strength meter

## Author

**Keerthika Selvam**
- GitHub: [@Keerthika546](https://github.com/Keerthika546)
- LinkedIn: [keerthika-selvam-](https://linkedin.com/in/keerthika-selvam-/)
