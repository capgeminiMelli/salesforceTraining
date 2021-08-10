## Salesforce CPQ Plugins
Salesforce CPQ Plugins let you add customized functionality to features within the salesforce CPQ package. 

![[Pasted image 20210806140341.png]]

-   **[Javascript Quote Calculator Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_dev_jsqcp_parent.htm)**  
    Add extra functionality to the quote line editor in Salesforce CPQ with custom JavaScript code. Seven available methods allow you to change how calculations are performed and manage page-level security such as field visibility.
-   **[Product Search Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_product_search_plugins.htm)**  
    The Salesforce CPQ product search plugin is an interface that you can implement to customize product search results in the Product Search page and the Guided Selling page. The plugin methods vary slightly between Product Search and Guided Selling implementations.
-   **[Recommended Products Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_recommended_products_plugin.htm)**  
    Use the Recommended Products plugin to recommend related products based on the existing products on a quote.
-   **[External Configurator Plugins](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_external_config.htm)**  
    Developers can set up links to third-party web applications from within the configurator or quote line calculator. You can open links through custom actions or with an automatic launch through a pluggable configurator.
-   **[Legacy Quote Calculator Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_legacy_quote_calculator_plugin.htm)**  
    Use Apex code to perform calculations within the CPQ quote line editor.
-   **[Product Configuration Initializer for Guided Selling](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_product_config_initializer.htm)**  
    The product configuration initializer uses a custom user-provided APEX page to select options and set field values based on the results of guided selling prompts. It works only for standard product option fields and not for configuration attributes or custom product option fields.
-   **[Product Search Executor for Guided Selling](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_product_search_executor.htm)**  
    A Product Search Executor plugin filters the results of a guided selling prompt after a sales rep’s input. It consists of a Visualforce controller and Visualforce page, which you can associate with a specific quote process within a guided selling configuration. It’s useful if you want to add an extra level of guided selling product filtering beyond what sales reps can control.
-   **[Document Store Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_doc_store_plugin.htm)**  
    Use a CPQ document store plugin to store your quote documents as custom objects or in third-party integrations.
-   **[Custom Action Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_custom_action_plugin.htm)**  
    A custom action plugin lets you run code before or after custom actions in Salesforce CPQ. Currently, custom action plugins support only cloning actions.
-   **[Salesforce CPQ Electronic Signature Plugin](https://developer.salesforce.com/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/docs/atlas.en-us.cpq_dev_api.meta/cpq_dev_api/cpq_esp_plugin.htm)**  
    An electronic signature plugin lets developers add electronic signature functionality to their orgs. This is useful for organizations who wish to streamline processes involving signatures, such as finalizing purchases and contracts.
	
	- [[ Billing ]]