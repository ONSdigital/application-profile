# Human vs Machine readability in JSON-LD API Responses

As JSON-LD serialises RDF, it is a powerful tool to provide linked data in API responses. Machine readability through RDF allows resources to be enumerated with easy-to-read URIs (i.e. <https://ons.gov.uk/datasets/cpih/editions/2019-07/version/2> for the seccond version of the CPIH dataset for July 2019) and API resposnes with JSON-LD context to fully describe that particular resource. If additional context and related resources are desired, subsequent calls to the endpoint for those resources can be made. However, when human users interact with APIs, they often need context upfront to understand the relationships between resources, so discretely responding for an individual resource may not be appropriate.

## Introducing Windowing

We use a concept we call "Windowing" with JSON-LD to provide context in API responses, especially when users request specific objects like dataset editions or versions. This way we deliver a response that not only includes the details of the requested object but also provides necessary contextual information about its parent or child objects, enhancing the understanding of the dataset structure.

For example, important context about the quality assurance performed on an edition (i.e. whether it is a National Statistic) would not be returned if a user requested information about a specific version or distribution. However, if the response has additional context about the edition, the user can understand the quality assurance status of the version or distribution by way of its relationship to the edition.

## Key Concepts

There are several important factors when considering windowing a JSON-LD API response, and they depend not only whether the response is intended for human or machine consumption but also on whether the request is for a named resource or a collection of resources.

### Contextual Understanding

When a user requests a specific dataset edition or version, windowing allows the response to include relevant information about its relationship to parent or child objects. This helps human users, understand the a particular version in relation to its parent edition and all the distributions a version may have.

### Human-Centric View

Windowing is particularly beneficial for making complex dataset relationships understandable for human users. It allows the API to deliver a focused response that includes only the necessary context for the requested object.

### JSON-LD Specificity

When using JSON-LD for machine readability, the goal is to provide all the necessary details for the requested object while avoiding the inclusion of redundant information. In this case, machine-readable data should remain precise and free from duplication, so these responses should be focused exclusively on the requested resource.

## Practical Application

- **Example Use Case**: If a user requests a specific version of a dataset, the windowed JSON-LD response will include all relevant details about that version, with references to its parent edition and related child distributions, especially detail about the dataset which is only captured at the edition and dataset levels. This ensures that users can understand usage notes, license information, and other attributes which would otherwise be missing from a focused response.
