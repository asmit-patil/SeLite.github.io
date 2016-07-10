---
layout: default
---
{% include links %}
* TOC
{:toc}

# Selenese terminology

## command
A step in Selenese [script]. See also {{navAutoGeneratedSeleneseCommands}} and [Selenium IDE documentation](http://docs.seleniumhq.org/docs/02_selenium_ide.jsp) > [Selenium Commands – “Selenese”](http://docs.seleniumhq.org/docs/02_selenium_ide.jsp#selenium-commands-selenese]).

## Making terms not test-specific
Selenium and SeLite are not test-specific. However, Selenium IDE GUI and its documentation refers to some features with word _test_. The following terms make it more general.

## case
_Case_ stands for _test case_. It consists of Selenese [commands][command] and comments. It's an `.html` file with a special format.

## suite
_Suite_ stands for _test suite_. It refers to (_contains_) one or more [cases][case]. It's an `.html` file with a special format.

A suite and any of its cases don't have to be in the same folder. Therefore a case can belong to multiple suites. If a case defines any [functions][function], other cases in the same suite can reuse them.

## script
When some functionality applies to both [cases][case] or [suites][suite], SeLite calls them _scripts_. To differentiate them from Javascript (or other scripts), they are sometimes called _Selenese scripts_. Some other terms are at [TestMethods](TestMethods) and [TestMethodsTheory](TestMethodsTheory).

Side note: [SelBlocks](https://addons.mozilla.org/en-US/firefox/addon/selenium-ide-sel-blocks/versions/) used to call Selenese _functions_ (defined by `function...endFunction`) _scripts_. (Originally they were defined by `script...endScript`.) However, both SelBlocks and [SelBlocksGlobal](SelBlocksGlobal)/SeLite refer to them as _functions_ rather than _scripts_.

## function
Word _function_ can refer to a Javascript `function` (whether in Selenium Core scope or not), or to a _function_ defined by [SelBlocksGlobal](SelBlocksGlobal)/SelBlocks construct `function...endFunction`. Where it's unclear, let's call the later _Selenese function_ or _script function_.

## set
_Set_ is a configuration set as per [Settings](Settings) > [Modules and sets](Settings#modules-and-sets).

## Core scope
_Selenium Core scope_, or just _Core scope_, is global scope (as in [JavascriptEssential](JavascriptEssential) > [Scope](JavascriptEssential#scope)) in _Core extensions_ and in Selenese _scripts_.

Implementation notes:

* _Core scope_ is the same as `selenium` object.
* See also [ExtensionSequencer](ExtensionSequencer) > [Global symbols and strict mode](ExtensionSequencer#global-symbols-and-strict-mode).

## Core extension
_Selenium Core extension_, or just _Core extension_, extends functionality available to Selenese scripts. It doesn't provide any visual interface. Generally it can be loaded from Selenium IDE or Webdriver. But even if a Core extension is for Selenium IDE only, it's called a _Core extension_ rather than _IDE extension_. Core extensions from SeLite are like that: they are Selenium IDE-specific and they don't work with Webdriver.

## IDE extension
_Selenium IDE extension_, or just _IDE extension_, extends GUI of Selenium IDE. It doesn't interfere with Selenese scripts. However, it may provide configuration or other interface used by a _Core extension_, and those can be packaged together in a Firefox add-on.

## Extension of Selenium IDE
This is either a _Core extension_ but for Selenium IDE only, or an _IDE extension_.

# Test terminology

## app DB
_App DB_ is a database (ideally, but not necessarily, in SQLite) used by the automated web application.

## script DB
_Script DB_ is a database (in SQLite) used by [scripts][script]. (It's not a DB of/containing _scripts_.) When used in automated testing, it is the test's expected/assumed version of the application data. It's usually populated from an (optionally filtered) export of [app DB]. See [TestMethodTheory](TestMethodTheory) > [Terminology](TestMethodTheory#terminology).

## vanilla DB
_Vanilla DB_ is a database (in SQLite) used for reloading [script DB] and [app DB]. It requires [app DB] to be in SQLite. It's a snapshot of exported [app DB], to which you can revert [script DB] when the [script] and app get out of sync.