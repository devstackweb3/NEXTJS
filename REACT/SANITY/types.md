# How to personalize a type in SANITY? 
Types permits to be reused as in react with reusable react components. They are  models of creation of texts, titles or images format that can be displayed on the web interface.

## STEP 1 | Type creation: 
Create a new typescript file in the schemaTypes folder.

## STEP 2 | Type configuration (details):
Import the 2 defineField and defineType library components from Sanity. 

Declare the default export as defineType. 

```
// subdescription.ts file
import {defineField, defineType} from 'sanity'

export default defineType({
  name: 'subdesc',
  title: 'SubDescription',
  type: 'document',
  fields: [
    defineField({
      name: 'subtitle',
      title: 'SubTitle',
      type: 'string',
    }),
    defineField({
      name: 'subdescription',
      title: 'SubDescription',
      type: 'blockContent',
    }),
  ],
})
```

## STEP 3 | Import the type created in the main view (article): 
The type represented can be an array of sub-descriptions made up of a title and customisable text (type: blockContent). In this way, importing the sub-description type allows me to reuse several blocks of text in the form of paragraphs, each separated by a title. 

```
import {defineField, defineType} from 'sanity'

export default defineType({
  name: 'article',
  title: 'Article',
  type: 'document',
  fields: [
    defineField({
      name: 'date',
      title: 'Published at',
      type: 'datetime',
    }),
    defineField({
      name: 'h1',
      title: 'Title',
      type: 'string',
    }),
    defineField({
      name: 'description',
      title: 'Description',
      type: 'string',
    }),
    defineField({
      name: 'slug',
      title: 'Slug',
      type: 'slug',
      options: {
        source: 'title',
        maxLength: 96,
      },
    }),
    defineField({
      name: 'author',
      title: 'Author',
      type: 'reference',
      to: {type: 'author'},
    }),
    defineField({
      name: 'image',
      title: 'Main image',
      type: 'image',
      options: {
        hotspot: true,
      },
    }),
    defineField({
      name: 'categories',
      title: 'Categories',
      type: 'array',
      of: [{type: 'reference', to: {type: 'category'}}],
    }),
    defineField({
      name: 'intro',
      title: 'Introduction',
      type: 'blockContent',
    }),
    defineField({
      name: 'subdescriptions',
      title: 'SubDescriptions',
      type: 'array',
      of: [{type: 'reference', to: {type: 'subdesc'}}],
    }),
  ],

  preview: {
    select: {
      title: 'title',
      author: 'author.name',
      media: 'mainImage',
    },
    prepare(selection) {
      const {author} = selection
      return {...selection, subtitle: author && `by ${author}`}
    },
  },
})

```

## FINAL STEP: 
Access to index.ts -> import the file previously created (subdesc.ts) -> export by default mode, within the schemaTypes term

```
import blockContent from './blockContent'
import category from './category'
import article from './article'
import author from './author'
import subdesc from './subdesc'

export const schemaTypes = [article, author, category, blockContent, subdesc]
```
