# CTags in rails

```sh
gem install ripper-tags

ripper-tags -R --exclude=tmp # will index all .rb files
```

note janus vim has C-Tags by default

# Basic usage 

## Change file type

...or tell vim to use other language code syntax

```
:set filetype=markdown
:set filetype=ruby
```

## Normal mode

Copy Paste

```
y         # copy
P         # paste in fron of word
p         # paste on position wher you are

```

movement

```
B b h <>l w W									# word movement
0 ^ gE ge <> e E $						        # home 
g0 g^ <gm> g$									# whole line home
42gg alebo 42G								    # go to line 42

{   }										    # start and end of paragraf
(   )											# start and end of sentence
```

scroll

```
zt zz zb    									#scroll top midle bottom
H  M  L
ctrl+e   ctrl+y                                 #clasik scrolling
```

Replace

```
R                                               #replace mode. Replace everything you type
                                                # Backspace will rollback changes 
```

## Visual mode

By visual mode some people refers to "highlite" or visual block mode (visually highlight 
text). The key part is that you can call commands while text is selected this way.

```
u                                               # Lovercase
U                                               # Upcase text
r                                               # replace selected with...; also check for `R`
```


# Advanced examples

### Edit multiple lines on certain position

There is command `Ctrl+q` that works similar as  as `v` (visual select bolck mode). By pressing it you can navigate
through out of the text (`jj`, `kk`, `hh`, `ll`) selecting multiple lines several cels of text.

![Select multiple lines in position with Vim][1]

**Add text on multiple lines**

* After selecting text this way you can pres `I`
* insert text
* press `escape`

**Remove text on multiple lines**

* After selecting text this way you can pres `d`



sources:

* http://vim.wikia.com/wiki/Inserting_text_in_multiple_lines

published 18.09.2013




### Sort words in vim

visual select block of lines and trigger 

    call setline('.', join(sort(split(getline('.'), ' ')), " "))

example

    a o e b x p
    :'<,'>call setline('.', join(sort(split(getline('.'), ' ')), " "))
    a b e o p x
    
sources:

*http://stackoverflow.com/questions/1327978/sorting-words-not-lines-in-vim

published: 18.09.2013




### remove duplicate lines



    :sort u

example:

```
aa
bb
cc
aa
dd

:sort u

aa
bb
cc
dd
```

sources: 

* http://vim.wikia.com/wiki/Uniq_-_Removing_duplicate_lines

published: 18.09.2013





### Rename ruby class name to method name

...or how to change capitalized constant strings to underscore strings

```vim
:s/[A-Z]/_\l\0/g
```

```
#before    
StaticDocumentForm

#after
_static_document_form
```

I'm to lazy to figure out the leading underscore :)


### Get rid of ^M in code

    :%s/^M//g

































[1]: https://raw.github.com/equivalent/scrapbook2/master/assets/images/2013/vim_scrap_replace-multiple-lines-on-position.png
