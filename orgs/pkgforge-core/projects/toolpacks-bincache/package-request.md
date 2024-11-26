---
description: How to request a new Package
icon: block-question
---

# Package-Request

{% hint style="info" %}
* This is only for people who can't write their own [<mark style="color:purple;">**`.SBUILD`**</mark>](broken-reference)
* If you want to try: [https://docs.pkgforge.dev/sbuild/instructions](https://docs.pkgforge.dev/sbuild/instructions)&#x20;
{% endhint %}

***

### Guide

{% hint style="info" %}
There's no strict rules, however if you put in **some effort**, it **will be Resolved Sooner**

* Also make sure you **do not request an already existing package**
* Check using [<mark style="color:orange;">**soar**</mark>](https://soar.qaidvoid.dev/search)

```bash
soar search "${PKG_NAME}"
```

* Search it on [**Github**](https://github.com/pkgforge/soarpkgs/tree/main/packages): [https://github.com/pkgforge/soarpkgs/tree/main/packages](https://github.com/pkgforge/soarpkgs/tree/main/packages)
{% endhint %}

* [x] What is the **Name of the Package** ? [<mark style="color:orange;">**(.pkg)**</mark>](../../../../sbuild/specification/2.pkg.md)&#x20;
* [x] Do you know the **AppID** ? [<mark style="color:orange;">**(.app\_id)**</mark>](../../../../sbuild/specification/4.appid.md)
* [x] What is **Type of the Package ?&#x20;**<mark style="color:orange;">**(**</mark>[<mark style="color:orange;">**appbundle**</mark>](../../../../formats/packages/appbundle/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**appimage**</mark>](../../../../formats/packages/appimage/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**archive**</mark>](../../../../formats/packages/archive-tbd/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**dynamic**</mark>](../../../../formats/binaries/dynamic/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**flatimage**</mark>](../../../../formats/packages/flatimage/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**gameimage**</mark>](../../../../formats/packages/gameimage-tbd/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**nixappimage**</mark>](../../../../formats/packages/nixappimage/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**runimage**</mark>](../../../../formats/packages/runimage-tbd/)<mark style="color:orange;">**|**</mark>[<mark style="color:orange;">**static**</mark>](../../../../formats/binaries/static/)<mark style="color:orange;">**)**</mark>
* [x] Can you **describe** what the Package does ?  <mark style="color:orange;">**(**</mark>[<mark style="color:orange;">**.description**</mark>](../../../../sbuild/specification/8.description.md)<mark style="color:orange;">**)**</mark>
* [x] What are the links to the Package's homepage/website? [<mark style="color:orange;">**(.homepage)**</mark>](../../../../sbuild/specification/11.homepage.md)
* [x] What is the link to this Package's [**Repology**](https://repology.org/projects/) ? [<mark style="color:orange;">**(.repology)**</mark>](../../../../sbuild/specification/17.repology.md)
* [x] What is the link where we can download it? [<mark style="color:orange;">**(.src\_url)**</mark>](../../../../sbuild/specification/18.sourceurl.md)
* [x] Can you classify this app using some [**tags**](../../../../sbuild/specification/19.tag.md)? [<mark style="color:orange;">**(.tag)**</mark>](../../../../sbuild/specification/19.tag.md)

{% hint style="info" %}
1. Once You have gathered the above information, [Create an Issue](https://github.com/pkgforge/soarpkgs/issues/new/choose): [https://github.com/pkgforge/soarpkgs/issues/new/choose](https://github.com/pkgforge/soarpkgs/issues/new/choose) `>>` [**Package Request (Generic)**](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=pkg-request\&projects=\&template=package-request--generic-.md\&title=%5BPackage+Request%5D+NAME_OF_PKG+%28TYPE_OF_PKG%29)
2. Replace with actual values; **Title**: **`[Package Request] NAME_OF_PKG (TYPE_OF_PKG)`**
3. Body: Fill with correct/Relevant Values from the Information you gathered
{% endhint %}
