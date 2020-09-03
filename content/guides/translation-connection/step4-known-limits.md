# Known limits

## Only text attributes

Our [suggested method](step3-interact-with-julia.html) allows your online Translation solution to translate only **textual** attributes of Akeneo PIM products.

Among other PIM attributes, Akeneo PIM has a `file` type attribute that allows to handle a binary file (CSV, DOC, DOCX, MP3 or PDF) associated with  the product.

A possible improvements of your connector could be also to take into account some of these files in order to translate them.

## Assets and Reference Entities

In the Akeneo PIM attribute type list, some specific attributes are used to associate data structures with PIM products and that themselves contain attributes that can be translated:
* [Assets](https://help.akeneo.com/pim/serenity/articles/what-about-assets.html) (Asset collection attributes)
* [Reference Entities](https://help.akeneo.com/pim/serenity/articles/what-about-reference-entities.html) (Reference Entity single or multiple links attributes)

### Assets

Let's talk about PIM assets first.

An asset can contain **a media** (an image, a video or a file) and can have **some metadata** too.

It would be interesting to propose to Julia to translate these **metadata asset attributes** and why not... some media.

You need to know that PIM assets can be used in 2 different ways:
* either **by associating the PIM with a DAM solution**: assets then come from this external solution.
* either by creating these assets **directly in the PIM**

In the first case, assets are usually translated **directly in the DAM** software. As a result, **Julia doesn't need to translate her PIM assets** because this have already been done by the DAM teams.

In the second case, it makes more sense: like products, the metadata of the assets could have been created in a source locale and **Julia might want to translate them into other locales**.

The main problem is that with the method we suggested, Julia can only indicate products that are to be translated (and not assets).

:::warning
This is due to the fact that there is no yet `Bulk action` on assets.
:::

Of course, by retrieving Julia's PIM products, you could also retrieve the information from the associated assets but this will not be very convenient for Julia.

Moreover, since a same asset can be used in several products, it could lead to the translation of assets that have already been translated.

:::info
Don't hesitate to [join us on Github](https://github.com/akeneo/pim-api-docs) if you find a workaround for this limit, we will add it to this guide!
:::

### Reference entities

A reference entity records have also localizable attributes and your connector, as for assets, could be legitimate to offer an associated translation service to Julia...

But for the same reasons as for assets (no `Bulk action` for reference entities and a reference entity record can be associated to several products), it is complicated to build this feature for Julia.

:::info
Again, don't hesitate to [join us on Github](https://github.com/akeneo/pim-api-docs) if you find a workaround for this limit, we will add it to this guide!
:::