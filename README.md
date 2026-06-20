# Developing search term synonyms based on Ovid MeSH term Scope Note

## Introduction

When conducting a comprehensive search of medical literature, the use of Medical Subject Headings (MeSH) to retrieve articles tagged with relevant medical concepts is often recommended.

To improve search coverage, search statements can be further complemented by including synonyms associated with the MeSH terms. Below are the steps I have learned for extracting relevant synonyms via Ovid's MeSH term scope notes.

## Step: Identify synonyms

1. Head to Ovid Medline search engine (OvidSP).

1. Switch to `Advanced Search` tab.

1. Select `Keyword`.

    ![Goto Advanced Search and select Keyword](static/img/image.png)

1. Make sure `Map Term to Subject Heading` is checked.

1. Enter keyword, e.g. `Periodontitis`.

1. Click `Search`.

    ![alt text](static/img/image-1.png)

1. In the results of Subject Heading mapping (titled `Your term mapped to the following Subject Headings`), click on the Subject Heading to view the MeSH term using the Subject Heading tree view.

1. Alternatively, click the `i` icon (under the `Scope` column) to view the scope note.

    ![alt text](static/img/image-2.png)

1. In the Subject Heading tree view, scope note can be accessed by clicking the `i` icon (under the `Scope Note` column).

    ![alt text](static/img/image-3.png)

1. In the Scope Note page, extract the synonyms under `User For` heading: 

    ![alt text](static/img/image-4.png)

## Step: Comprehensive search

To perform a comprehensive search using Ovid Medline on periodontitis (for example): 

1. We use the MeSH term (i.e. `periodontitis/`).

    The trailing slash `/` signifies an exact subject heading search. It tells Ovid to look in the official subject heading field for `periodontitis`. It automatically includes any articles tagged with the narrower subject headings beneath it in the subject heading hierarchy.

1. We also combine the search with the following synonyms:

    ```
    pericementitides OR
    pericementitis OR
    periodontitides
    ```

    Which can be further simplified using the truncation syntax into:

    ```
    (pericementiti* OR periodontitide*).mp.
    ```

    `.mp.` stands for "multi purpose" for Ovid, by default it includes multiple field searches like title, abstract and keywords ([link](https://ospguides.ovid.com/OSPguides/medline.htm#mpalias)).

1. Combine all of the above using the `OR` operator:

    ```
    periodontitis/ OR
    (pericementiti* OR periodontitide*).mp.
    ```

### Optional: Separate Step 1 and Step 2

The search steps (Step 1 and Step 2) can be performed separately in the Ovid search form. By separating the steps, you will be able to visualise how many additional records that were retrieved via synonyms.

At the time of writing:

- `periodontitis/` returned `24,875` hits
- `(pericementiti* or periodontitide*).mp.` returned `21` hits
- `1 or 2` returned `24,890` hits

![search history for separate steps](static/img/image-5.png)

This means that the `mp` search using synonyms returned an additional `15` records.


## Credits

Credit goes to Dr. Ainol Haniza binti Kherul Anuwar, who originally taught me this method. She learned this technique during her tenure at the Malaysian Health Technology Assessment Section (MaHTAS), Ministry of Health Malaysia.

At the time of writing, Dr. Ainol is a senior lecturer in the Department of Community Oral Health & Clinical Prevention, Faculty of Dentistry, Universiti Malaya, Malaysia ([link to CV](https://umexpert.um.edu.my/ainolhaniza)).
