---
tags: coding, law, society
feed: show
---

# Links
- [[Room for Growth]]

# Sources
- Abe Voelker's blog - [GitLaw: GitHub for Laws and Legal Documents - a Tourniquet for American Liberty](https://blog.abevoelker.com/gitlaw-github-for-laws-and-legal-documents-a-tourniquet-for-american-liberty/)
- Being considered by the French Government - [forum.etalab.gouv.fr](https://forum.etalab.gouv.fr/t/gitlaw-using-version-control-software-to-build-laws-collaboratively/2622)
- EU - [European Parliament to share amendment web tool as open source](https://joinup.ec.europa.eu/news/european-parliament-share)

This post will start with the history of [GitHub](https://github.com/) and [Git](https://git-scm.com/), founded on the 3rd April 2005, by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds)<sup>1</sup>. Once upon a time code started to be written. It would be written for websites, operative systems, games, and many other uses. As software got more complex it was harder to manage. It required multiple people working on the same project, and tight cooperation amongst the developers. It all got so complex that it was impossible for anyone to know how it worked in all its detail. As with everything, programming errors were made. When it broke, we first had to understand exactly what was the problem. Then we had to fix the code, but navigating code we don't understand takes a long while, let alone knowing how to fix it without breaking other parts of the software. This is when Git and other Software Management tools came to help.

# Improvements made by Git and other Source Code Management tools

## Automatically saving a product's history
GitHub works by keeping the software's history using a simple interface. There is a central repository (we'll call it origin) with the code. A pull request is the same as asking for the latest code version. When I have the code I make commits with comments explaining the changes made. There is a diff operator that allows me to see the changes made between commits (So we can just look at the code changes, instead of having to look at the entire code). When we are done with changing the code we make a push request, which equates to sending our branch to the origin and asking for it to be accepted. Others can see the uploaded code, see the changes committed and make comments on things that are not clear / can be improved. Once all the comments are answered we can finally merge the code.

PS: The above is a simplification of the process, written with clarity for those who never worked with Git over correctness of all processes. For a detailed and fully correct explanation see [GitFlow](http://datasift.github.io/gitflow/IntroducingGitFlow.html).

## Branching of a software to test different hypothesis
I can create 2 branches of a software (i.e. make 2 exact copies of the master code), make different changes and see which branch performs better. After choosing the 'best' branch I can make a pull request from it to the master branch, and discard the 'losing' branch.

## Faster collaboration by working on different parts of the code
Following the methodology above, I can make a pull request and work on component A of the code. You make a pull request and work on component B. We both make a push request and have our requests evaluated independently.

## Code reviews became a lot easier with git diff
As described above, after making the necessary code changes and a pull request, other developers will be able to see the changes made and comment on them, while focusing exclusively on the code differences.

## Accountability of individual changes
Whenever a change is made, we can trace back who committed the change. That way any doubts regarding the thought process that lead to the code implementation and related questions can be directed easily, making it faster to understand 'old' code.

# So how does this relate to law?
Law is code, and code is law.

Code is a set of rules that computers follow in order to attain the expected goal. As users require new functionalities and better performance the code gets harder to manage and organize. Code complexity has a cost on its own: it makes it harder for new people to understand and improve. Hence we need source code management tools such as Git.

Law is a set of rules that people follow in order to attain the best for society<sup>2</sup>. As human interactions get more complex the law gets more complex in order to handle all the edge cases. Law complexity has a cost on its own: bureaucracy makes it harder for new businesses to start, transactions to be made and its' final user, the average citizen, loses track of what he can, can't and should do. Hence we need Law Management tools such as GitLaw.

# What is GitLaw?
GitLaw is a project. It is a project that promises to give transparency and accountability to the legislative branch, while speeding up the process and allowing easier citizens contributions.

# How is GitLaw achieving what it promises?

## Transparency
Firstly, by having all laws available in a central website, we can easily search for all laws and law books<sup>3</sup>. Secondly, by having the history of law books available we can trace back changes to those who pushed for them to happen. This would avoid the problem of joining bills so that law changes are made as a bundle, where some small changes are passed without being given proper thought. By allowing for frequent yet shorter bills to be voted independently we bring visibility to the smaller changes.

## Accountability
By checking history we can back trace changes done to those who pushed for them. This should make everyone think twice before pushing for a bill change. It adds moral costs (people should think through changing laws more carefully since they are accountable for what they push) while decreasing bureaucratic costs.

## Reducing costs of new bills
Following the above, it decreases bureaucratic costs: Managing bills and push requests online reduces management costs, and being able to see law changes as difference files reduces the time wasted to understand what a new bill is doing.

## Speeding up the process
Frequently bills are proposed as a list of planned changes. If it passes then a team of lawyers will change law books accordingly. Under GitLaw the government changes the law directly and bills are just the difference files.

Remark: Even though we should be fast to consider and approve new bills, the stability of laws is very important if we want to foster events. Ideally bills would be passed but only became 'valid' every x months or so (as a group), so that it wouldn't keep changing constantly. However this detail and others can and should be more thoroughly though about after implementing GitLaw, since this problem is independent of whether or not we are using GitLaw.

## Ease of use
GitHub requires learning, but almost every developer uses it because it quickly pays off for how easy maintaining code becomes. Similarly GitLaw would require a learning phase (probably no more than a few hours), but after that we would be able to see the law at a specific period in time, see who advocated for each bill, check the discussions had before passing each bill to know how well it was though about.

# That all sounds great, but how do we implement it?
This is the tricky part (as with everything). Personally I have no doubts about the usefulness of such system, but for any change to go through there must be people pushing for it to happen. Society benefits as a whole (and a lot), but there is no one who benefits enough to push for it. In order to bring interest to it either we find a great bunch of philanthropists willing to put in the hours (ideal but usually unlikely given how many other problems we have to work on), or we need to find either public funding or a sustainable business model to implement this.

## Step 1: Developing a law book filetype ( LawBook )
The most similar occurrence of this is [Fountain](https://fountain.io), as mentioned in [Abe Voelker's blog](https://blog.abevoelker.com/gitlaw-github-for-laws-and-legal-documents-a-tourniquet-for-american-liberty/). The idea is simple: instead of having PDFs, Microsoft Word / Google Docs or another general purpose filetype to edit law books, we should have a specific one designed for exclusively for laws. The format of law books does not differ significantly from each other. I would compare it to designing a syntax for Screenplays similar to what [Fountain](https://fountain.io) achieved.

The filetype should have metadata such as creation date, author, owner and others included. In the file itself we should be able to define sections, sub sections,... and reference each other. This part needs to be better thought about, but ideally we would need at least a lawyer involved (to enlighten us about how to generalize a law book's structure) and a programmer (ideally someone who is familiar with parsing documents, to avoid possible problems). Maybe a variation of markdown would be ideal.

Remark: It is common to define the meaning of certain words to avoid ambiguity, such as in the [RFC2119](https://www.ietf.org/rfc/rfc2119.txt). We could just have all such defined words link to their definition, decluttering space.

Ideally we would end with a page like [Fountain's Syntax Page](https://fountain.io/syntax), which explain how to write with this syntax.

## Step 2: Developing a web / local editor
The LawBook we defined above could directly be edited via a text editor, but we want to make it easier and more intuitive to use. As such we need a text editor. It would need to allow:
* Add sections / subsections and others.
* References to other sections
* Add word definitions (or link to word definitions in other documents)
* Warn about broken links, since we might point to a document and after a while that document is changed, rendering the link invalid.
* (Optional) Reference to other law books.
* etc

It should be as plain to use as possible. Keeping it simple will make it easier to use. That's why I personally prefer a web based editor, but this is up to debate.

## Step 3: LawBook to pdf
Essential for easy printing / sending rulebooks to people. Shouldn't be hard to implement. Since we are aiming this pdfs for possible printing then we need to think carefully how to resolve both internal links and links to other LawBooks.

## Step 4: Setup with Git
Setup a repository, create a few LawBooks and make changes, see how it behaves.

## Step 5: Build GitLaw
Probably the hardest part. GitLaw would be the effective GitHub for Law, a browser based editor where people could see the central repository branches, diffs, comments, push requests (i.e. bills) and everything else. This also needs to be well though of before implementing. A good starting point is to analyze GitHub functionality and see where it has unneeded and/or missing features for the GitLaw needs.

## Step 6: Move LawBooks to GitLaw
All publicly available LawBooks can be moved to GitLaw, without the need for legal permission (after all LawBooks are already publicly available).

Having an easy to read online LawBook reader is crucial to bringing people's attention to the tool. If it is easier to use than tracking all the law books scattered through different institutions then it will be used.

## Step 7: Give repositories ownership to the respective institutions
Allow institutions to alter the LawBooks themselves. We need good tutorials on how to use the tools we provide, but this project should be straightforward.

# Do you think the above will happen?
Yes. Steps 1 to 3 shouldn't be too hard with part time investment. Step 4 is incredibly hard and probably will require full time investment. Maybe discussing the possibility with GitHub itself would make it easier. Maybe not. Step 5 is time consuming but isn't hard. Step 6 is the easiest one if we advertise our goal during the process. All of the above should be made into an MVP, and then improve on that by iterating over the various steps. By starting as a lookup tool with history (for lawyers to see the current laws and nothing else), it should get some traction.

# Footnotes
<sup>1</sup> Git - [How it actually came to be](https://en.wikipedia.org/wiki/Git#History) instead of the short tale I tell.
<sup>2</sup> If this is the one and only goal of having laws is debatable, but lets assume this is true for now. Hopefully it isn't too far from this.
<sup>3</sup> By law book I mean a document where a set of laws are written. Law book sounds weird, but I didn't find a better term. Tell me if you know the actual name for those.