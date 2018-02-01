These are terms specific to Sitecore Experience Commerce such as Minions, Commerce Engine, Commerce Business Tools, etc.

Commerce Business Tools: The Commerce Business Tools are a set of rich business tools for merchandisers and customer service representatives. The business tools are built on the Angular framework.

Commerce Core: Commerce Core is a lightweight framework that provides core application capabilities in an encapsulated package. The Core does not itself offer any commerce capabilities; commerce-related functionality is enabled through plugins that depend on the Core functionality.

Commerce Engine: The Commerce Engine is an extensible commerce core framework, hosting commerce services such as Cart, Order, Pricing, Promotions, Catalogs and Inventory.

Content Foundation: TO DO: DEFINE

Activity: Part of Commerce Core. An internal construct that wraps a specific set of work for activity tracking, for example, for reporting and performance.

Approval: Part of Commerce Core. Basic approval commands and pipelines to facilitate a basic approval process. Approvals are used by pricing and promotions to seek the approval of changes before implementing.

Authentication: Part of Commerce Core. The ability to authenticate a call to the service API using certificates.

Bootstrap: Part of Commerce Core. Commands and pipelines to support bootstrapping the solution

Entities:

Caching: Part of Commerce Core. Commands and pipelines to support in-memory caching.

Command: Part of Commerce Core. Basic structure for supporting the concept of commands. A command acts like the API in a task-driven API.

Components:

Policies:

Commands:

Lists:

Minions:

List Membership:

List Minions:

Environments:

Pipelines:

Rules:

Eventing:

Logging:

Caching:

Plugins:



SXA Storefront: The Sitecore Experience Accelerator \(SXA\) Storefront is a sample storefront website that is integrated with the Commerce Engine.



 Component: Basic structure for supporting compositional extensibility, including the component class and various base components. 

 Context: A call-level context called CommerceContext, which is initialized when a call enters the service and is carried throughout the service call. The CommerceContext provides an object cache, messaging, headers, and other core call-level information. 

 Controller: Basic controllers that make core functionality available through the Service API. 

 Converter : Custom JSON converters for the Service API. 

 Entity: Commands, policies, and pipelines to support reading and writing commerce entities. A CommerceEntity is a core artifact designed to directly represent a business concept, which is stored as a single unit in a persistent storage. Entities have identifiers and can be retrieved through the Service API. 

 Environment: Commerce environments provide the ability to have separately configurable pools of data and service functionality that run together in a single-service instance. Environments can share the same persistent store as other environments or be separated into their own exclusive persistent store. 

 Event: Basic infrastructure to support events and event-driven actions. 

 Exception: Basic CommerceException base class. 

 Globalization: Commands and their pipelines to support globalization, including support for multicurrency and localization. 

 List: Commands and pipelines to support basic list functionality, including basic list management. Use ManagedLists to track lists of entities either based on their state or based on activities that need to be performed on them. Lists are used to provide organizational structure and to support business processes. 

 Location: Commands and pipelines to support locations, for example, retrieving supported countries and country information. 

 Logging: Support for core logging using SeriLog and to specify logging using Microsoft Application Insights. 

 Media: Core classes to support media types and policies, including a GlobalImagePolicy and an image class. 

 Minion: Commands and pipelines to support minions including the MinionBoss and RunMinion pipelines, and the policies to support configuring minions in the environment configuration. 

 Model: Basic core models, which are POCO classes that are reusable inside entities and components. Models can be used to present data as part of a command response, in the models collection. Models are listed in the Sitecore.Commerce.Documentation.chm \(in the SDK folder\) on the Model Class page. 

 Node: A node is a running instance of the Service API. Core pipelines, blocks, and policies that enable basic node functionality. 

 Performance: Commands and policies to support tracking and integrating with performance counters for commands. 

 Pipeline: Core commands and models to support pipeline functionality. Pipelines, in turn, leverage the Sitecore.Framework.Pipelines infrastructure. 

 Plugin: Core support for the Commerce pluggable extensibility. 

 Policy: A named, versionable and variable set of data that can be used as facts within behaviors to influence behavioral outcomes. This provides an auditable mechanism for viewing, simulating, and changing core decision criteria that might be used by business processes or other policy-driven behavior. Various plugins have specialized policies to add additional facts to existing policies and/or new policies, or to implement new concepts, such as dynamic pricing.  

	Worker processes only need a link to the policy store to bootstrap.  Single point of truth for policies.  Publish workflow without moving data.  Policies are heavily cached and rarely change.  Policies can have attached rules to deliver personalized policies. 

	Policies are listed in the Sitecore.Commerce.Documentation.chm \(in the SDK folder\) on the Policy Class page. 

Policy characteristics include:  Centralized policy store using abstract entity storage. 



Provider: Core interfaces for an EntityProvider and an IndexProvider. The concept of a provider is avoided because any plugin could potentially be a provider. This is only used by the FileSystemProvider, which enables reading a CommerceEntity from the file system. 

ServiceApi: Core models and policies to enable the basic Service API. 

Transaction: Core functionality to support transactionality in the solution. 

 

 Commerce Entity Store: A Commerce EntityStore is an abstract mechanism for specifying the persistence and retrieval of Commerce entities. The EntityStore provides a customization point that allows you to customize where and how entities are persisted. Sitecore XC uses an SQL-based EntityStore. 

A Commerce EntityStore is policy-driven and leverages plugins for persistence





commerce entity \(entity\): A commerce entity represents a core unit of persistence in the form of a POCO class that inherits from commerce entity and can extend the entity along with behavior defined based on lifecycle events of the entity or defined commands. 

	Commerce entities are designed to be serialized rapidly into JSON and stored in a variety of persistent stores. 



	Namespace: The first part of the entity’s unique identifier \(string\). 

	Id : Its unique identifier \(string\). 

	Name : Name of the entity \(string\). 

	FriendlyId: Human readable instance of the unique identifier \(string\). 

	DisplayName : Displayable name of the entity \(Localized&lt;String&gt;\). 

	DateCreated: Date and time the entity was created, automatically updated \(DateTime\). 

	Description: Description of entity \(Localized&lt;String&gt;\). 

	DateUpdated: Date and time the entity was updated, automatically updated \(DateTime\). 

	Policies: List of policies applicable to this entity \(List&lt;Policy\). 

	Components: List of components applicable to this entity \(List&lt;Component&gt;\). 

	ListMemberships: Delimited list of lists names \(string\). 

	SortOrder: The order this item is sorted \(string\). 

	IsDeleted: Flag to signify that the item is deleted \(Bool\). 

	IsPersisted: Flag to signify that the item is persisted \(Bool\). 

	DateDeleted: Date and time that the entity was deleted \(DateTime\). 

 

Compositional extensibility: Compositional extensibility is a simple class supplied by plugins as a way of extending a commerce entity. Components can be added or removed by a plugin into a commerce entity by adding to the components property. This is usually done via a PipelineBlock or a RuleAction. 

 

Managed Commerce List: A managed commerce list represents a core mechanism for organizing and relating commerce entities. Sitecore XC supports simplistic named lists as well as more tightly managed lists. Lists can be curated by selecting individual members of the list or implemented as expressions against the search provider for dynamic listing. 





