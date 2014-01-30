View location conventions for Nancy that add "-mobile" suffix to view names when request is from mobile devices

# Usage

Just set it up in your Bootstrapper

	protected override void ConfigureConventions(global::Nancy.Conventions.NancyConventions nancyConventions)
	{
	    base.ConfigureConventions(nancyConventions);

	    // Set up mobile view conventions
	    Nancy.Conventions.MobileViewLocationConventions.Enable(nancyConventions);
	}
