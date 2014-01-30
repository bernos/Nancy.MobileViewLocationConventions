View location conventions for Nancy that add "-mobile" suffix to view names when request is from mobile devices

# Usage

Just set it up in your Bootstrapper

	:::c#
		protected override void ConfigureConventions(global::Nancy.Conventions.NancyConventions nancyConventions)
		{
		    base.ConfigureConventions(nancyConventions);

		    // Set up mobile view conventions
		    Nancy.Conventions.MobileViewLocationConventions.Enable(nancyConventions);
		}

Your best bet will be to add the MobileViewLocationConventions _after_ all other conventions. This is because the mobile conventions actually proxy through to any existing conventions and add the '-mobile' suffix to the view names returned by your existing conventions.

# Setting up views

To provide a mobile-specific version of your view, simply create a version of your existing view, with the '-mobile' suffix in the filename.

For example, assuming you had a `~/Views/Home/Index.cshtml` simply create `~/Views/Home/Index-mobile.cshtml` and that will be used when the convention detects a mobile device

# Mobile device detection

Currently, mobile detection is implemented by matching the incoming user agent header to a regex. The regex can be configured in your app.config file by adding and editing the following app setting

	:::xml
		<add key="Nancy.MobileViewLocationConventions.MobileUserAgentRegex" value="/Mobile|iP(hone|od|ad)|Android|BlackBerry|IEMobile|Kindle|NetFront|Silk-Accelerated|(hpw|web)OS|Fennec|Minimo|Opera M(obi|ini)|Blazer|Dolfin|Dolphin|Skyfire|Zune/" />