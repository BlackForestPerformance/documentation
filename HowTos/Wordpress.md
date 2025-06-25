---
title: WordPress
layout: default
parent: How To
---

# WordPress
{: .no_toc}
#### Table of Contents
{: .no_toc}
1. TOC
{:toc}

## Log into the WordPress Admin Panel

{: .warning-title }
> You need this for every other step in this document.

{: .info-title }
> What you need
>
> Someone with credentials to access the Admin Panel of the WordPress installation. These are in the Marketing and in the Admin Collection on Vaultwarden.

1. Navigate to the [WordPress admin panel]
2. Log in with the credentials you have.

## Add new Post

1. [Log into the WordPress Admin Panel](#log-into-the-wordpress-admin-panel)
2. Now when you visit the website, you can see the Admin Bar at the top of the page.
3. In the Admin Bar, select "New" > "Post"
4. For car posts, select the car category in the right sidebar, for other posts, select "uncategorized" or create a new category.

## Edit sites, Pages, and Posts

1. [Log into the WordPress Admin Panel](#log-into-the-wordpress-admin-panel)
2. Now when you visit the website, you can see the Admin Bar at the top of the page.
3. There will be the corresponding menu item depending on the type of page you currently look at.
   - For sites, select "Edit Site" in the Admin Bar
   - For pages, select "Edit Page" in the Admin Bar
   - For posts, select "Edit Post" in the Admin Bar

## How to use the WordPress Editor (in general)

1. [Edit sites, Pages, and Posts](#edit-sites-pages-and-posts)
2. You will now see the WordPress Editor, which is a block-based editor.

Explaining this editor is beyond the scope of this document, but you can find a lot of resources online.\
Just know that you have blocks for every element you want to add to the page.

You can content blocks, like paragraphs, images, embeddings, etc. and layout blocks, like columns, groups, etc.\
Content blocks display content, the layout blocks are used to structure the page and place the content blocks inside them.

There rarely is a right or wrong way to do it, just play around with it until you are satisfied with the result.

## Add a "Team \[Semester]" Page

{: .info }
> In theory, you don't have to do it this way, but this way is known to work somewhat reliably.

1. Add the new page. The Slug should be `team-[semester]`, e.g. `team-2023` or `team-2023-2024`.
2. In the right sidebar, select the template "Page with title - fullwidth".
3. Copy the content of an existing team page
4. Change the images and text to the new team members.
5. On the team overview page (the one where all team pages are listed), you can duplicate the newest entry and edit the first one.
6. Make sure the Button for the navigation is working.
7. Now select Edit Site in the Admin Bar.
8. Click on the header and select "Edit".
9. Select the navigation block on the right.
10. You should now see the tree of the links in the right sidebar.
11. Click on the plus to add the page you just created and drag and drop it to the right position in the navigation.
12. Save all changes and confirm everything works.

----
[WordPress admin panel]: https://.bfp-racing.de/wp-admin/