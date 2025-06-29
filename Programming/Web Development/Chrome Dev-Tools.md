# Chrome Dev-Tools

## Inspector

- Activated either with F12 or 3 dots → More Tools → Developer Tools
- Used to look at all the information on a site such as HTML, CSS, Cookie info, errors, list of Event Listeners, and more

## View, edit, and delete cookies

- Http cookies are used to mange user sessions and store preferences
- Within dev tools Applications → Storage → Cookies

### Fields

- Name - cookies name
- Value - cookies value
- Domain - host that takes said cookie
- Path - the URL that must be in the URL request to send `Cookie` header
- Expires / Max-Age - expiration date  for maximum age for a cookie unless the is a session cookie then it’s value is always `Session`
- Size - cookie’s byte size
- HTTP -  If true the cookie would only be used over HTTP with no javascript modifications
- Secure - If true the cookie would only be sent over HTTPS connections
- SameSite - value is `strict`or `lax` if the cookie is using the experimental `SamSite`
- SameParty - if  true this field means the cookie is allowed to be set or sent in contexts where all ancestor frames belong to the same First-Part Set
- Priority - contains low, medium, high if using deprecated cookie Priority attribute

### Edit a cookie

- Name, value, Domain, Path, and Expires / Max-Age are editable

### Delete a cookie

- Cookies can be deleted individually or all cookies can be cleared from a site

## View and change CSS

- An element can be inspected by right clicking a spot on a web page and selecting inspect. This well highlight the element in the **DOM Tree**

## Classes

- can be added to elements through dev-tools by inspecting an element clicking .cls (top right hand corner) classes can be ad from there
- From there you can also toggle classes

## Adding a pseudostate

- adding a pseudostate can be done by inspecting an element then selecting `:hov`
- supported pseudostates are:
    - :active
    - :focus
    - :hover
    - :visited

### Change the diemensions of an element

- WIthin the styles tab there is a Box model that showls the margin, border, and padding of an element
- Box Models accept values in either precentage or vw otherwise it defaults to px