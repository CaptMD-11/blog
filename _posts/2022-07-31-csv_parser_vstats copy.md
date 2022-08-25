---
layout: post
current: post
cover: assets/images/csvparser3.png
#cover: assets/images/bluebackground.jpg
navigation: True
title: VCSV
date: 2022-07-31 10:18:00
tags:
class: post-template
subclass: 'post'
---

Using VStats to analyze CSV files. 

I've always wanted to make VStats practical for everyday use. Inputting arrays could work for small data sets, but what about larger data sets that contain thousands of entries? Surely you can't expect one to enter all that manually into an array. So I decided to write a class allowing users to access VStats functions on CSV files without manually inputting anything. 

The VCSV class parses the data from what are essentially <samp>String</samp> lines to arrays, using the <samp>Scanner</samp> class and some other utilities. Here is some code I wrote for returning a column of numbers from a CSV: 


<pre class="s-code-block language-java">
    // 0-based index logic
    public static double[] getColumnOfNumbers(String fileName, int col) {

        File file = new File(fileName);
        ArrayList&lt;Double&gt; res = new ArrayList&lt;Double&gt;();

        try {
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            line = scanner.nextLine();

            while (line.length() != 0) {
                if (col == 0)
                    res.add(Double.parseDouble(line.substring(0, line.indexOf(","))));
                else if (col == getNumCols(fileName) - 1)
                    res.add(Double.parseDouble(line.substring(line.lastIndexOf(",") + 1)));
                else
                    res.add(Double.parseDouble(
                            line.substring(getNthIndexOf(line, col, ",") + 1, getNthIndexOf(line, col +
                                    1, ","))));
                line = scanner.nextLine();
            }

        } catch (Exception e) {
            System.out.println(e);
        }

        double[] output = new double[res.size()];
        for (int i = 0; i < res.size(); i++) {
            output[i] = res.get(i);
        }
        return output;

    }
</pre>

I plan to make VCSV another library like VStats with <samp>static</samp> methods so that users don't have to create objects of the class. 

We'll see how far this goes! 