# Test Book

Basically the citations work as follow:

We have a 'literature.bib' file, where you enter each citation giving it a unique 'tag' with all the required information. For example, the syntax is:

@misc{ROC,
  TITLE = {The Rights of Christ according to the principles and doctrines of the Children of Peace},
  AUTHOR = {Willson, David},
  YEAR = {1815},
  URL = {https://archive.org/details/cihm_62453}
}
 
@misc{TLW,
  TITLE = {The Late War between the United States and Great Britain},
  AUTHOR = {Hunt, Gilbert J.},
  YEAR = {1816},
  URL = {https://github.com/wordtreefoundation/books/blob/master/pseudo_biblical/The%20Late%20War%20-%20Gilbert%20Hunt%20-%201816.md}
}

So for our first citation the unique tag is 'ROC' and for the second, 'TLW'. So now when I want to cite then in text, all I do is use the unique tag along with the 'cite' filter. For example:


Here is some sentence citing "The Rights of Christ ..."" citation {{ "ROC" | cite }}. 

Or another sentence using "The Late War ..."" citation {{ "TLW" | cite }}.

These would be rendered as:

Here is some sentence citing "The Rights of Christ ..."" citation [1]. 

Or another sentence using "The Late War ..."" citation [2].

Finally, when I want to create an aggregated 'End References' page, all I do is add the tag:

{% references %} {% endreferences %}

And it will render all the citations from the literature.bib file in numerical order (**which corresponds to the order they are listed in the literature.bib file, not necessarily the order they appear in the book**). Assuming we populate the literature.bib file in the order references appear in the book (which won't be too much overhead), the final references will correspond to the order of citations throughout the book. 

Let me explain more about how the numbering works:  So the literature.bib file is deserialized as a javascript array of 'citation' objects.  Basically I've made it so that the citations are created based on the index of the citation object in the array, thus they are uniquely numbered.  I thought this was important because, in the event you want to cite the same reference in multiple places, it will maintain the same citation number and link to the same unique location in the End References.  It also allows us the flexibility to add new citations simply by adding them to the literature.bib file in the correct location, and since the index has changed everything will auto increment.






