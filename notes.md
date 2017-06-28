React Router DOM provides two components:

_BrowserRouter_, the root routing component that keeps your UI in sync with the URL
_Route_, which is responsible for rendering a component in your app when the URL matches its path.

You began declaring routes with react router by rendering a router that wraps all your app components.

```
<BrowserRouter>
	<div className="container">
		<Route path="/" component={Home}/>	
	</div>
</BrowserRouter>
```

**BrowserRouter and Route**

BrowserRouter wraps all of your app's components. So for react-router, you will need a component, which can include all 
of the other components of your app.

Route - matches the url specified in the path attribute.
When a path starts with '/', react router assumes it to be starting from home page. and hence adds the home page component along with the 
actual component rendered.
E.G -- > /about, will render both <Home/> and <About/> components.

To avoid this, we use the 'exact' keyword, to let React know that we want to render the component for '/', only if the path is exactly '/'.

You can also use render attribute for ```<Route />```

render attribute is preferred over to component, because with render you can pass props to the component that we want to render.
```
<Route path="/about" render={ () => <About title="About Us"/>}
```
	
-------------

*NavLink and Link*

To add navigation support to your app, you can use _NavLink_ or _Link_.

```<Link>``` or ```<NavLink>```, are used instead of the ```<a>``` tags. While rendering the component, React will automatically render this tags as ```<a>``` tags.
You can specify the path you want to navigate to with **_to_** attribute. Again, like _Route_, here also you can use the **_exact_** keyword to match
the exact url.

```<NavLink>``` adds an **_active_** class to the currently selected link itself. You can write your own styles to this 'active' class. However, if you want to have a custom class name for the active link, you need to use the **_activeClassName_** attribute.
```
<NavLink path="/about" activeClassName="myactiveclass">About</NavLink>
```

You can also write active styles directly to the ```<NavLink>``` component using the **_activeStyle_** attribute.
```
<NavLink exact to="/" activeStyle={{backgroundColor:'tomato'}}</NavLink>
```

**Redirect**
The _Redirect_ component tells the react-router to redirect from one route to another. 

_Redirect_ requires a **_to__* prop and the value should be the url to redirect to.

To avoid issues while dealing with deeply nested routes, use a ```<Route/>``` to **render** a redirect component that will navigate to the new location.
