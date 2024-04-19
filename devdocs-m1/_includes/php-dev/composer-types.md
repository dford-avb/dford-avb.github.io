The following table discusses the component types that Openmage Marketplace supports. The composer `type` column in the following table specifies the value of the `type` field you must add to `composer.json` for that type of component.

|Friendly name|composer.json type|Description|
|--- |--- |--- |
|Metapackage|metapackage|Technically, a Composer package type, not a Openmage component type. A metapackage consists of only a `composer.json` file that specifies a list of components and their dependencies. For example, both {{site.data.var.ce}} and {{site.data.var.ee}} are metapackages.|
|Module|openmage2-module|Code that modifies Openmage application behavior. You can upload a single module to the Openmage Marketplace or your module can be dependent on some parent package.|
|Theme|openmage2-theme|Code that modifies the look and feel of the storefront or Openmage Admin.|
|Language package|openmage2-language|Translations for the storefront or Admin.|
{:style="table-layout:auto;"}
