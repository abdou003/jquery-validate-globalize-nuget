jquery-validation-globalize-nuget
=============

NuGet Package for **jQuery Validation Globalize Plugin**

This is just the source for [jQuery Validation Globalize](https://github.com/johnnyreilly/jquery-validation-globalize), and I just packed the sources and assets to work with ASP.NET MVC projects.

## Usage Instructions ##

Just add a reference to `/Scripts/jquery.validate.globalize.js` or `/Scripts/jquery.validate.globalize.min.js` right after `jquery-{version}.js`, `jquery.validate.js`, `cldr.js` and `globalize.js` (or the respective minified versions of these files), directly or via bundling: 

**Direct Example**

    <script type="text/javascript" src="/Scripts/jquery.validate.js"></script>
    <script type="text/javascript" src="/Scripts/jquery.validate.unobtrusive.js"></script>
    <script type="text/javascript" src="/Scripts/cldr.js"></script>
    <script type="text/javascript" src="/Scripts/globalize.js"></script>
    <script type="text/javascript" src="/Scripts/jquery.validate.globalize.js"></script>
    <script type="text/javascript" src="/Scripts/jquery.validate.globalize.js"></script>

**Bundling Example**

At `/App_Start/BundleConfig.cs`:

    public static void RegisterBundles(BundleCollection bundles)
    {
        ...
    
            var bundle = new ScriptBundle("~/bundles/jqueryval") { Orderer = new AsIsBundleOrderer() };

            bundle
                .Include("~/Scripts/jquery.validate.js")
                .Include("~/Scripts/jquery.validate.unobtrusive.js")
                .Include("~/Scripts/cldr.js")
                .Include("~/Scripts/globalize.js")
                .Include("~/Scripts/jquery.validate.globalize.js");
            bundles.Add(bundle);

        ...
    }

`AsIsBundleOrderer` can be implemented like this:

	using System.Collections.Generic;
	using System.Web.Optimization;

	namespace YourProject.Infrastructure
	{
    	public class AsIsBundleOrderer : IBundleOrderer
    	{
        	public IEnumerable<BundleFile> OrderFiles(BundleContext context, IEnumerable<BundleFile> files)
        	{
            	return files;
        	}
    	}
	}

# License

As the original repository, this NuGet package is under [MIT License](http://opensource.org/licenses/mit-license.php).