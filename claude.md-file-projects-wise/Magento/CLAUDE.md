# CLAUDE.md - Magento 2 Project Instructions for Claude Code

---

## 🏗️ Project Overview

### Magento 2 Project Details
- **Magento Version**: 2.4.4-p13
- **PHP Version**: 8.1
- **Environment**: Development
- **Database**: MySQL 8.0.43
- **Composer Mode**: Developer
- **Deployment Mode**: Developer

### Project Architecture
- **Theme**: Custom theme located in `app/design/frontend/`
- **Primary Language**: English (update with your store language)
- **Multi-store Setup**: [Yes/No - describe if applicable]
- **Key Integrations**: Payment gateways, third-party APIs, Multi-Inventory, Product page customization with Plan Page, Checkout & backend customization and many more.
- **Custom Extensions**: Multiple custom extensions exist in `app/code/` directory

---

## 📁 Magento 2 File Structure Understanding

### Core Directory Structure
```
app/
├── code/                    # Custom modules and third-party extensions
├── design/                  # Custom themes
├── etc/                     # Application configuration
└── i18n/                    # Translation packages

pub/
├── static/                  # Generated static files
├── media/                   # Uploaded media files
└── errors/                  # Custom error pages

var/
├── log/                     # Application logs
├── cache/                   # Cache files
├── session/                 # Session files
├── tmp/                     # Temporary files
└── generated/               # Auto-generated code

vendor/                      # Composer dependencies
bin/magento                  # CLI tool
```

### Custom Code Locations
- **Custom Modules**: `app/code/[Vendor]/[ModuleName]/`
- **Custom Themes**: `app/design/frontend/[Vendor]/[ThemeName]/`
- **Custom Configuration**: `app/etc/config.php`, `app/etc/env.php`

---

## 🎯 Magento 2 Development Standards & Best Practices

### Module Development Standards
- **Follow Magento 2 Coding Standards** strictly
- **Use Service Contracts** for all public APIs
- **Dependency Injection** instead of ObjectManager
- **Repository Pattern** for data access
- **Factory Pattern** for object creation
- **Plugin Pattern** preferred over preferences/rewrites

### Module Structure Standards
```
app/code/[Vendor]/[Module]/
├── Api/                     # Service contracts (interfaces)
├── Block/                   # View layer blocks
├── Controller/              # MVC controllers
├── Cron/                    # Cron job classes
├── Helper/                  # Helper classes (use sparingly)
├── Model/                   # Business logic and data models
│   ├── ResourceModel/       # Database interaction layer
│   └── Source/              # Source models for admin options
├── Observer/                # Event observers
├── Plugin/                  # Plugins/interceptors
├── Setup/                   # Installation/upgrade scripts
├── etc/                     # Module configuration
│   ├── module.xml           # Module declaration
│   ├── di.xml               # Dependency injection
│   ├── events.xml           # Event configurations
│   ├── crontab.xml          # Cron configurations
│   └── adminhtml/           # Admin-specific configs
├── view/                    # View layer files
│   ├── adminhtml/           # Admin panel views
│   └── frontend/            # Frontend views
└── registration.php         # Module registration
```

### Naming Conventions
- **Modules**: `[CompanyName]_[ModuleName]` format
- **Classes**: PascalCase with descriptive names
- **Methods**: camelCase starting with verb
- **Constants**: UPPER_SNAKE_CASE
- **Database tables**: `[prefix]_descriptive_name`
- **Config paths**: `section/group/field` format
- **Event names**: `[area]_[module]_[action]_[when]`

---

## 📝 Claude Code Usage Instructions

### Preferred Development Workflow
1. **Analysis**: "Analyze the existing [functionality] in this Magento 2 project"
2. **Planning**: "Following Magento 2 best practices, create a plan for [enhancement]"
3. **Implementation**: "Implement the solution following our CLAUDE.md guidelines"
4. **Code Review**: "Review this code for Magento 2 standards compliance"

### Essential Context for All Requests
- Always mention this is a **Magento 2 project**
- Reference **specific Magento version** when relevant
- Consider **multi-store setup** if applicable
- Follow **upgrade-safe practices**
- Implement **proper error handling and logging**
- Consider **performance implications**

---
## 🚨 Critical Magento 2 Rules

### What to NEVER Do
- ❌ **Never modify core Magento files** in `vendor/magento/`
- ❌ **Never use ObjectManager directly** except in factories
- ❌ **Never hardcode store/website IDs** or URLs
- ❌ **Never skip proper module dependency declaration**
- ❌ **Never modify vendor third-party files** directly
- ❌ **Never use SQL queries directly** without collections/repositories
- ❌ **Never create tables without setup scripts**
- ❌ **Never bypass ACL in admin controllers**

### What to ALWAYS Do
- ✅ **Always use plugins/observers** for core modifications
- ✅ **Always implement proper error handling** and logging
- ✅ **Always declare module dependencies** in module.xml
- ✅ **Always use factories** for object creation in business logic
- ✅ **Always consider multi-store compatibility**
- ✅ **Always follow upgrade-safe practices**
- ✅ **Always validate and sanitize user input**
- ✅ **Always use proper ACL** for admin functionality
- ✅ **Always implement caching** for expensive operations
- ✅ **Always use translations** for user-facing text

---

## 💡 Development Tips

### CLI Commands
```bash
# Essential Magento CLI commands
bin/magento setup:upgrade
bin/magento setup:di:compile  
bin/magento setup:static-content:deploy
bin/magento cache:clean
bin/magento cache:flush
bin/magento module:enable Vendor_Module
bin/magento module:disable Vendor_Module
```


---

## 📋 **Technical Guidelines**

### **Our Custom Coding Standards**

#### **PHP Development Standards**
- **Follow PSR-2 standards** with Magento extensions for all PHP Code
- **Use CamelCase** for class names, **camelCase** for methods and variables
- **Use short array syntax** `[]` instead of `array()`
- **Order imports alphabetically** and group by namespace
- **For dependencies**, favor constructor injection, use type hints
- **Handle exceptions properly** - never suppress or swallow them
- **Use PHP 8.1+ features** where possible
- **Always use constructor property promotion**
- **Always declare parameter types and return types** in methods
- **Don't add return types** to functions that need to abide by an interface (models, resource models, collections, etc.)
- **Always add proper type casting for integer returns** in model classes:
  - For nullable integer fields: `return $this->getData(FIELD) ? (int) $this->getData(FIELD) : null;`
  - For required integer fields: `return (int) $this->getData(FIELD);`
- **Add line break** to the end of files
- **Add @throws tags** to docblocks for exceptions, where appropriate
- **Use trailing commas** for all arrays and method arguments
- **Import all classes** with use statements rather than using FQCNs
- **Do not add copyright headers**, but add line break and `declare(strict_types=1)` to top of each PHP class
- **Don't nest arrays on single line** - always use multi-line format for readability
- **Always add extra line breaks** between conditions and before return statements, unless only statement in block
- **Always add an extra line break** after `parent::__construct` calls
- **Methods that contain one or no parameters** break curly brackets onto a new line
- **Methods with multiple parameters** should have parameters on new lines with trailing commas

### **Adobe Commerce Technical Guidelines**

#### Basic Programming Principles
- **Function arguments MUST NOT** be modified
- **Explicit return types MUST** be declared on functions
- **Type hints for scalar arguments SHOULD** be used
- **All new PHP files MUST** have strict type mode enabled by starting with `declare(strict_types=1);`
- **All updated PHP files SHOULD** have strict type mode enabled

#### Class Design Standards

- **Object decomposition MUST** follow SOLID principles
- **Object MUST** be ready for use after instantiation - no additional public initialization methods allowed
- **Factories SHOULD** be used for object instantiation instead of `new` keyword
- **Class constructor** can have only dependency assignment and/or argument validation operations
- **Constructor SHOULD** throw exception when validation of argument has failed
- **Events MUST NOT** be triggered in constructors
- **All dependencies MUST** be requested by the most generic type required
- **Proxies and interceptors MUST NEVER** be explicitly requested in constructors
- **Inheritance SHOULD NOT** be used - composition SHOULD be used for code reuse
- **All non-public properties and methods SHOULD** be private
- **Abstract classes MUST NOT** be marked as public `@api`
- **Service classes SHOULD NOT** have mutable state
- **Only data objects or entities MAY** have observable state
- **"Setters" SHOULD NOT** be used (only allowed in DTOs)
- **"Getters" SHOULD NOT** change object state
- **Static methods SHOULD NOT** be used
- **Temporal coupling MUST** be avoided
- **Method chaining MUST** be avoided
- **Law of Demeter SHOULD** be obeyed

#### **Dependency Injection**

- **There SHOULD** be no circular dependencies between objects
- **app/etc/di.xml MUST** contain only framework-level DI settings
- **All modular DI settings SHOULD** be stored in `<module_dir>/etc/di.xml`
- **All modular Presentation layer DI settings SHOULD** be stored in `<module_dir>/etc/<area_code>/di.xml`


#### Interception Standards
- **Around-plugins SHOULD** only be used when behavior substitution is needed
- **Plugins SHOULD NOT** be used within own module
- **Plugins SHOULD NOT** be added to data objects
- **Plugins MUST** be stateless
- **Plugins SHOULD NOT** change state of intercepted object

#### Exception Handling Standards
- **All exceptions MUST** produce error messages with: Symptom, Details, Solution/workaround
- **Exceptions MUST NOT** be handled in same function where thrown
- **Exceptions MUST NOT** handle message output
- **Business logic MUST NOT** be managed with exceptions
- **Exception class short name MUST** be clear and meaningful
- **Thrown exceptions SHOULD** be as specific as possible
- **All third-party library communications MUST** be wrapped with try/catch
- **`\Exception` SHOULD** be caught only in code calling third-party libraries
- **`\Exception` SHOULD NOT** be thrown in Controllers
- **Separate exceptions hierarchy SHOULD** be defined on each application layer
- **It is NOT allowed** to absorb exceptions with no logging
- **Exceptions SHOULD NOT** be caught in loops
- **Methods using system resources MUST** use try/finally blocks
- **Exceptions displayed to users MUST** be sub-types of `LocalizedException`

#### Security Standards
- **Use prepared statements** for SQL queries
- **Implement multi-factor authentication** where possible
- **Do not ship with default credentials**
- **Implement weak-password checks**
- **Sanitize input; escape output**
- **Follow XSS prevention strategies**
- **Cast incoming data** to expected type
- **Check incoming string data length**
- **Drop special characters** from incoming string data
- **Modules with Admin functionality should have ACL**
- **Do not include unused libraries/frameworks**
- **Catch and log exceptions/notices/warnings**
- **Don't display error output to users**
- **Utilize CSRF tokens mechanism**
- **Use POST requests** for data manipulation
- **Frequently update third-party libraries**
- **Don't trust user-submitted path/file requests**
- **Don't use dangerous functions**: `eval()`, `passthru()`, `system()`, etc.
- **Secure files** by web server configuration

#### JavaScript Application Standards
- **UI Component framework MUST** be used for frontend applications
- **Only private content SHOULD** be rendered in browser
- **All RequireJS module dependencies MUST** be declared
- **Follow W3C Content Security Policy**
- **Follow ESLint rules**
- **Use ECMAScript 5.1** as JS standard
- **Use language features** for private state (no underscore naming)
- **All XMLHttpRequest MUST** be asynchronous
- **New global properties MUST NOT** be added
- **Modules MUST NOT** have external side effects

#### Testing Standards
- **Only public methods SHOULD** be tested
- **All objects SHOULD** be tested in isolation
- **ObjectManager MUST NOT** be used in unit tests
- **ObjectManagerHelper MAY** be used to mock dependencies

#### Configuration Standards
- **Code and Environment Configuration MUST NOT** be stored in Data Storage
- **Installation process MUST NOT** modify Code
- **All XML configuration formats MUST** be declarative
- **All Configuration objects MUST** use `Magento\Framework\Config`

#### Dependency Injection Standards
- **There SHOULD** be no circular dependencies between objects
- **app/etc/di.xml MUST** contain only framework-level DI settings
- **All modular DI settings SHOULD** be stored in `<module_dir>/etc/di.xml`
- **All modular Presentation layer DI settings SHOULD** be stored in `<module_dir>/etc/<area_code>/di.xml`

#### Interception Standards
- **Around-plugins SHOULD** only be used when behavior substitution is needed
- **Plugins SHOULD NOT** be used within own module
- **Plugins SHOULD NOT** be added to data objects
- **Plugins MUST** be stateless
- **Plugins SHOULD NOT** change state of intercepted object

#### Application Layer Standards

##### **All Layers**
- **Application SHOULD** be structured in compliance with CQRS principle
- **Every layer MUST** process exceptions of underlying layer
- **A layer MUST NOT** depend on layer above it

##### **Presentation Layer**
- **Request, Response, Session objects MUST** be used only in Presentation layer
- **All actions MUST** return `ResultInterface` implementation
- **Actions MUST NOT** reference blocks declared in layout
- **Blocks MUST NOT** assume specific controller was invoked
- **Templates MUST NOT** instantiate objects

##### **Data Access Layer**
- **Every persistence operation MUST** be performed with one scope set
- **Entities MUST NOT** contain persistence-related logic
- **MySQL strict_mode SHOULD** be aligned with latest MySQL release default

##### **Service Contracts Layer**
- **Service contract interfaces SHOULD** be placed in separate API modules
- **Service interfaces for web APIs MUST** be placed under `MyModuleApi/Api` directory
- **Service data interfaces MUST** be placed under `MyModuleApi/Api/Data`
- **Each service interface SHOULD** declare single public method
- **Service contracts SHOULD** support batch data processing
- **Batch retrieval operations MUST** accept `SearchCriteriaInterface`
- **Service data interfaces SHOULD** extend `ExtensibleDataInterface`
- **Services SHOULD NOT** apply ACL rules

#### Security Standards
- **Use prepared statements** for SQL queries
- **Implement multi-factor authentication** where possible
- **Do not ship with default credentials**
- **Implement weak-password checks**
- **Sanitize input; escape output**
- **Follow XSS prevention strategies**
- **Cast incoming data** to expected type
- **Check incoming string data length**
- **Drop special characters** from incoming string data
- **Modules with Admin functionality should have ACL**
- **Do not include unused libraries/frameworks**
- **Catch and log exceptions/notices/warnings**
- **Don't display error output to users**
- **Utilize CSRF tokens mechanism**
- **Use POST requests** for data manipulation
- **Frequently update third-party libraries**
- **Don't trust user-submitted path/file requests**
- **Don't use dangerous functions**: `eval()`, `passthru()`, `system()`, etc.
- **Secure files** by web server configuration

#### JavaScript Application Standards
- **UI Component framework MUST** be used for frontend applications
- **Only private content SHOULD** be rendered in browser
- **All RequireJS module dependencies MUST** be declared
- **Follow W3C Content Security Policy**
- **Follow ESLint rules**
- **Use ECMAScript 5.1** as JS standard
- **Use language features** for private state (no underscore naming)
- **All XMLHttpRequest MUST** be asynchronous
- **New global properties MUST NOT** be added
- **Modules MUST NOT** have external side effects

#### Testing Standards
- **Only public methods SHOULD** be tested
- **All objects SHOULD** be tested in isolation
- **ObjectManager MUST NOT** be used in unit tests
- **ObjectManagerHelper MAY** be used to mock dependencies

#### Configuration Standards
- **Code and Environment Configuration MUST NOT** be stored in Data Storage
- **Installation process MUST NOT** modify Code
- **All XML configuration formats MUST** be declarative
- **All Configuration objects MUST** use `Magento\Framework\Config`

### **PHP Coding Standards**

#### **Basic Standards**
- **Follow Magento Coding Standard** with PSR-1 and PSR-2 compliance
- **Use PHP_CodeSniffer** for code compliance checking
- **Use `::class` keyword** instead of string literals for class name resolution

### **DocBlock Standards**


#### **General Principles**
- **Be as short as possible** while including all necessary information
- **Follow phpDocumentor standard** formatting
- **Make code self-explanatory** with descriptive names

#### **Files**
- **Each source file MUST** have DocBlock header with short description
- **Separate descriptions** with empty lines

#### **Classes and Interfaces**
- **Classes SHOULD** have human-readable description
- **Use short form names** to encourage readability
- **Add use cases** where appropriate

#### **Class Attributes**
- **Class attributes MUST** have type declaration using `@var` tag

#### **Functions and Methods**
- **Typed method signature MUST** be preferred over PHPDoc annotations
- **Include meaningful information** beyond method name
- **Declare all arguments** using `@param` tag when needed
- **Use `@return` tag** only when method signature doesn't supply all info
- **Use `@throws` tag** for possible exceptions

#### **Constants**
- **Constants MAY** have short description if it adds value

#### **DocBlock Tags**
- **Use `@api` tag** for public API elements
- **Use `@deprecated` tag** with explanation for deprecated elements
- **Use `@var` inline tag** for IDE type hinting
- **Use `@method` tag** for magic methods

### **JavaScript Coding Standards**

#### **Formatting Standards**
- **Use 4 spaces** for indentation
- **Add single linefeed** at end of file
- **Max line length** is 120 characters
- **Use UNIX line termination** (LF)
- **Use string concatenation** for multi-line literals
- **Use braces** with all multiline blocks
- **Always use semicolons** as statement terminators
- **Use single quotes** for strings

#### **Naming Conventions**
- **Avoid underscores and numbers** in names
- **Use accurate descriptive names** for variables/methods
- **Private/protected methods** start with underscore
- **Function names** start with English verb
- **Use `get`/`set` prefix** for accessors
- **Use `has`/`is` prefix** for Boolean methods

#### **Additional Standards**
- **Put operators** on preceding line
- **Use semantic HTML markup** only
- **Use standard features** for portability
- **Avoid closures** attached to DOM elements
- **Use explicit scope** for clarity
- **Don't modify built-in objects**
- **Declare variables with `var`**

#### **Naming Conventions**
- **Widget names MUST** be camel case English words
- **Widget names SHOULD** be verbose enough to describe purpose

#### **Instantiation Standards**
- **Load additional JS files** using `$.mage.components()`
- **Use `$.mage.extend()`** to extend widget resources
- **Instantiate widgets** using `data-mage-init` attribute
- **Use `.mage()` plugin** for widgets with callbacks

#### **Development Standards**
- **Widgets SHOULD** comply with single responsibility principle
- **Widget properties MUST** be in options for configurability
- **Widget communications MUST** be handled by jQuery events
- **Use DOM event bubbling** for parent-child communication
- **Comply with Law of Demeter** principle
- **Don't instantiate widgets** inside other widgets

#### **Architecture Standards**
- **Use underscore prefix** for private methods
- **Start element selection** with `this.element`
- **Widget options SHOULD** have default values
- **Pass DOM selectors** as widget options
- **Use `_setOption` method** for state changes
- **Handle widget initialization** for successive calls
- **Clean up on destruction** to original state
- **Bind events** using `_bind()` method

### **JavaScript DocBlock Standards**

#### **JSDoc Requirements**
- **Document all files, classes, methods** with JSDoc
- **Use `//** for inline comments
- **Begin JSDoc** with `/**`
- **Enclose inline tags** in braces: `{@code this}`
- **Start block tags** on own line

#### **JSDoc Tags**
- **`@const`** - marks variable read-only
- **`@extends`** - indicates class inheritance
- **`@interface`** - indicates function defines interface
- **`@implements`** - indicates class implements interface
- **`@override`** - indicates method/property override
- **`@param`** - documents function arguments
- **`@return`** - documents return type
- **`@type`** - identifies variable/property type

### **jQuery Widget Coding Standards**

#### **Naming Conventions**
- **Widget names MUST** be camel case English words
- **Widget names SHOULD** be verbose enough to describe purpose

#### **Instantiation Standards**
- **Load additional JS files** using `$.mage.components()`
- **Use `$.mage.extend()`** to extend widget resources
- **Instantiate widgets** using `data-mage-init` attribute
- **Use `.mage()` plugin** for widgets with callbacks

#### **Development Standards**
- **Widgets SHOULD** comply with single responsibility principle
- **Widget properties MUST** be in options for configurability
- **Widget communications MUST** be handled by jQuery events
- **Use DOM event bubbling** for parent-child communication
- **Comply with Law of Demeter** principle
- **Don't instantiate widgets** inside other widgets

#### **Architecture Standards**
- **Use underscore prefix** for private methods
- **Start element selection** with `this.element`
- **Widget options SHOULD** have default values
- **Pass DOM selectors** as widget options
- **Use `_setOption` method** for state changes
- **Handle widget initialization** for successive calls
- **Clean up on destruction** to original state
- **Bind events** using `_bind()` method


### **LESS Coding Standards**


#### **General Rules**
- **Use 4 spaces** for indentation
- **Add space before** opening braces and line break after
- **Add line break** after each selector delimiter
- **Use single quotes** for strings
- **Add spaces** before and after combinators
- **Start each property** in new line
- **Add space after** but not before colon
- **Add blank line** at end of file and after selectors
- **Add semicolon** after property
- **Avoid `!important`** if possible

#### **Selectors**
- **Avoid `id` selectors**
- **Class names SHOULD** be lowercase, start with letter
- **Separate words** with dash '-'
- **Helper classes** start with underscore '_'
- **Use short but descriptive** class names
- **Use meaningful, specific** class names
- **Avoid qualifying** class names with type selectors
- **Type selectors MUST** be lowercase
- **Write selectors** in one line
- **Avoid more than 3 levels** of nesting

#### **Properties**
- **Sort properties** alphabetically
- **Use shorthand properties** where possible
- **Don't specify units** for "0" values
- **Omit leading "0"s** in values
- **Use lowercase** hexadecimal notation
- **Use 3-character hex** where possible
- **Avoid hex values** in properties - use variables

#### **Variables**
- **Local variables** in module file beginning
- **Theme variables** in `_theme.less` file
- **All variable names MUST** be lowercase
- **Value variables**: `@property-name`
- **Parameter variables**: `@component-element__state__property__modifier`

#### **Mixins**
- **Theme mixins** in `web/css/source` directory
- **Apply class naming rules** for mixins
- **Use double underscore** prefix for grouping
- **Set default values** for parameters

### **HTML Style Guide Examples**

#### **Basic Formatting**
- **Use 4 spaces** for indentation
- **Add blank line** at end of file
- **Always close** self-closing tags
- **Avoid lines longer** than 120 characters
- **Align tag attributes** one under another for readability

#### **Syntax Standards**
- **No spaces around** equals sign (recommended)
- **Use one space after** colon in attributes
- **Use appropriate HTML5** elements for blocks
- **Use semantic class names** and IDs
- **Avoid presentational** class names

#### **Accessibility & Standards**
- **Comply with WCAG 2.0** guidelines
- **Include microdata** on crucial pages


### **Code Demarcation Standards**

#### **Semantics**
- **Use meaningful lowercase words** with hyphens for attributes
- **Semantic representation** may rely on ID attribute
- **Follow separation** of presentation and content
- **Use semantic HTML markup** only

#### **Visual Representation Patterns**
- **Visual representation MUST** rely only on HTML class attributes
- **Use HTML class attributes** as first option
- **Don't hard-code CSS styles** in JavaScript
- **Don't use inline CSS styles** in HTML tags

#### **Business Logic**
- **Business logic MUST** rely on form/data attributes only
- **Assign HTML helper classes** in JavaScript
- **Helper class names** start with underscore and lowercase
- **Don't select DOM elements** based on HTML structure
- **Use jQuery templates** for recurring markup

---
## 🏷️ Common Magento 2 Patterns to Reference

### Factory Pattern Usage
```php
// Use factories for object creation
$product = $this->productFactory->create();
$collection = $this->collectionFactory->create();
```

### Event Observer Registration
```xml
<!-- events.xml -->
<event name="catalog_product_save_after">
    <observer name="custom_observer" instance="Vendor\Module\Observer\ProductSaveAfter"/>
</event>
```

### Plugin Registration
```xml
<!-- di.xml -->
<type name="Magento\Catalog\Model\Product">
    <plugin name="custom_product_plugin" type="Vendor\Module\Plugin\ProductPlugin"/>
</type>
```

---



## 🔌 Extension Development Patterns

### Admin Grids and Forms
```php
// Use UI Components for admin interfaces
// Create ui_component XML files
// Implement DataProvider classes
// Use proper admin routes and ACL
```
---

## 🚀 Performance & Optimization Guidelines

### Database Optimization
```php
// Use proper indexing
// Avoid N+1 queries in collections
// Use select specific columns when possible
$collection->addFieldToSelect(['field1', 'field2']);
```

### Code Optimization
- Use lazy loading where possible
- Implement proper factory usage
- Use plugins instead of preferences when possible
- Minimize object creation in loops

---


## 🎨 Theme Development Guidelines

### Theme Structure
```
app/design/frontend/[Vendor]/[theme]/
├── composer.json
├── theme.xml
├── registration.php
├── web/
├── Magento_Catalog/
├── Magento_Checkout/
└── templates/
```

### Template Inheritance
- Understand fallback mechanism
- Use proper template override structure
- Implement responsive design principles

---

## 🔍 Common Issue Areas & Solutions

### Performance Issues
- Check for N+1 queries in collections
- Implement proper caching strategies
- Optimize database queries
- Use flat catalog when appropriate

### Memory Issues
- Check for memory leaks in loops
- Optimize collection loading
- Use proper object cleanup

### Upgrade Issues
- Check for deprecated method usage
- Verify compatibility with latest Magento version
- Update composer dependencies

---
## 🔒 Security Best Practices

### CSRF Protection
```php
// Always implement CSRF protection in forms
$this->formKeyValidator->validate($request);
```

### ACL (Access Control Lists)
```xml
<!-- Always implement proper ACL -->
<resource id="Vendor_Module::resource_name" title="Resource Title" translate="title"/>
```

### SQL Injection Prevention
```php
// Use parameterized queries
$connection->select()->where('field = ?', $value);
```

---

## 🌍 Multi-Store Considerations

### Store Scope Configuration
```php
// Always consider store scope
$this->scopeConfig->getValue($path, \Magento\Store\Model\ScopeInterface::SCOPE_STORE, $storeId);
```

### Website/Store Context
```php
// Handle multi-store contexts properly
$this->storeManager->getStore()->getId();
$this->storeManager->getWebsite()->getId();
```

---

## 📊 Logging and Debugging

### Custom Logging
```php
// Implement proper logging
$this->logger->info('Custom log message', ['context' => $data]);
$this->logger->error('Error message', ['exception' => $e]);
```

### Debug Information
```php
// Use proper debugging techniques
$this->logger->debug('Debug info', ['data' => $debugData]);
```

### Log Files Locations
- `var/log/system.log` - General application logs
- `var/log/exception.log` - PHP exceptions
- `var/log/debug.log` - Debug information

---
## 🔧 Magento 2 Development Patterns

### Plugin Development
```php
<?php
// Preferred method for modifying core functionality
// Use Before, After, or Around methods appropriately
class ExamplePlugin
{
    public function beforeMethodName($subject, $arg1, $arg2) { }
    public function afterMethodName($subject, $result, $arg1, $arg2) { }
    public function aroundMethodName($subject, \Closure $proceed, $arg1, $arg2) { }
}
```

### Observer Pattern
```php
<?php
// Use for reacting to events
class ExampleObserver implements \Magento\Framework\Event\ObserverInterface
{
    public function execute(\Magento\Framework\Event\Observer $observer) { }
}
```

### Repository Pattern
```php
<?php
// Always implement repository interfaces
interface ExampleRepositoryInterface
{
    public function save(ExampleInterface $example);
    public function getById($id);
    public function delete(ExampleInterface $example);
    public function getList(\Magento\Framework\Api\SearchCriteriaInterface $searchCriteria);
}
```

### Service Contracts
```php
<?php
// Define clear interfaces for public APIs
interface ExampleManagementInterface
{
    /**
     * @param int $customerId
     * @return \Vendor\Module\Api\Data\ExampleInterface
     */
    public function processExample($customerId);
}
```

### Dependency Injection Configuration
```xml
<!-- di.xml for proper DI configuration -->
<preference for="Interface" type="Implementation"/>
<type name="ClassName">
    <arguments>
        <argument name="paramName" xsi:type="object">Class\Name</argument>
    </arguments>
</type>
```

---
