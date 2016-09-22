# Modules and Services
Alex Buckley

_The services mechanizm of the Java platform is not very well known_

## Introduction to Services
```
module java.desktop {
	requires java.xml; // module name

	exports java.awt; // package name
}
```

### Service Relationships
Looser coupling can be acheived with an interface in one module and an implementation in a separate module
 
```
// Consumer module
module java.desktop {
	requires java.xml;
	exports java.awt;

	uses javax.print.PrintServiceLookup; // type name
}

// Provider module
module printlib {
	provides javax.print.PrintServiceLookup;
	  with com.printlib.FastPrint; // 2 type names
}
```

### Using the Service Type in java.desktop
```
ServiceLoader<PrintServiceLookup> psls = 
  ServiceLoader.load(PrintServiceLookup.class);

for (PrintServiceLookup psl : psls) {
	PrintService ps = psl.getDefaultPrintService();
	if (ps.isDocFlavorSupported(...)) return ps;
}

return DEFAULT_PRINT_SERVICE;
```

### Designing a Service Type
```
interface PrintServiceLookup {
	PrintService getDerfaultPrintService();
	PrintService[] getPrintServices();
	PrintService[] getPrintServices(DocFlavor);
}

interface PrintService {
	DocFlavor[] getSupportedDocFlavors();
	boolean isDocFlavorSupported();
	void createPrintJob();
}
```

*The intent is that it be inexpensive to load and resolve `uses` classes for a module*

### Consumer and Provider modules are clear by syntax
 * It is also possible for a Consumer module to also Provide an imlpmeentation. 

### Sometimes useful to check annotations
```
Stream<Provider<PrintServiceLookup>> providers = 
  ServiceLoader.load(PrintServiceLookup.class)
	.stream()
	.filter(p -> p.type().isAnnotationPresent(...));

PrintServiceLookup psl = providers.map(Provider::get)
  .findAny()
	.orElse(DEFUALT_PRINT_SERVICE);
```

## Services for Optional Dependencies
```
// wishful
requires optional jdk.scripting.nashorn; // not valid
```

Instead it is better to create a service type module with an api for multiple implementations to provide implementations for 
```
module java.scripting {
	uses javax.script.ScriptEngineFactory;
	expoerts javax.scripting;
}

module java.scripting.nashorn {
	provides javax.script.ScriptEngineFactory
	  with jdk...;

		requires javax.scripting;
}

module groovy.scripting {
  provides javax.script.ScriptEngineFacotry
	  with groovy...;

	requires javax.scripting;
}
```

## Service Binding
Services interact with:
 * Strong encapsulation _provider modules do not export the package where the implementation lives_
 * Reliable configuration 

Binding happens when the module system looks for a provider for a user of an interface

## Summary
 * Service relationships are first class in the module system
 * 
