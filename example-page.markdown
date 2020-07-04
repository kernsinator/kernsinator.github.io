---
layout: single
title:  "Welcome to Jekyll!"
date:   2020-07-03 09:49:30 -0500
categories: jekyll update
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/


---
layout: single
title:  "Testing layouts"
date:   2020-07-03 09:49:30 -0500
categories: test
tags: testing
header:
  video:
    id: XsxDH4HcOWA
    provider: youtube
---


{% include video id="rs39FWDhzDs?start=110" provider="youtube" %}

{% highlight java %}
public boolean makeMove() {
        boolean moveMade = false;
        //get all available moves
        ArrayList<Integer> moves = getAvailableMoves(locRow, locCol);

        //pick a move - random

        if (moves.size() > 0) {

            //choose random move from available moves
            int randomMove = random.nextInt((moves.size()));
            int move = moves.get(randomMove);

            //place piece
            moveMade = placePiece(locRow + V_SHIFT[move], locCol + H_SHIFT[move]);

            // update current position
            locRow = locRow + V_SHIFT[move];
            locCol = locCol + H_SHIFT[move];

        } else {

            if (moveCounter == 64) {
                incrementCompletedTours();
            }

            if (moveCounter > maxTourLength) {
                maxTourLength = moveCounter;
            }

            if (moveCounter < minTourLength) {
                minTourLength = moveCounter;
            }

            tours[moveCounter]++; // add to frequency array
        }

        //if moves is empty return false
        return moveMade;
    }
{% endhighlight %}