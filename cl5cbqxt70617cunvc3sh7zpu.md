## VIM Editor

# What is Vim?

Vim is a text editor for Unix that comes with Linux, BSD, and macOS. It is known to be fast and powerful, partly because it is a small program that can run in a terminal (although it has a graphical interface). It is mainly because it can be managed entirely without menus or a mouse with a keyboard.

For the following five reasons, I feel people should use Vim:

1. It's omnipresent. You don't have to think about learning about several boxes with a new editor.
2. It is highly scalable. You can use it only to edit configuration files or become your entire forum for writing.
3. It has a shallow memory footprint.
4. It's command-centered. With a few commands, you can perform complex text-related tasks.
5. It is highly configurable and uses simple text files to store its settings.

# **Why Use Vim?**

In all POSIX systems, Vim is the default fallback editor. Vim is sure to be open, whether you have just installed the operating system, or you have booted into a minimal system repair environment, or you are unable to access any other editor. While you can switch out other tiny editors on your systems, such as GNU Nano or Jove, it's Vim that's all but guaranteed to be on every other system in the world.

In short, I think competence with Vim should be considered the way you view competence with your native language, or simple maths, etc. 

### How to use Vim

**Step 1:-** To open a file in VIM editor you just need to write `vim <filename> ` OR ` vi <filename> `.

![Screenshot from 2022-07-08 00-43-31.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657221502866/XLuioIzV-.png align="left")

Press Enter then your file will open in the VIM editor

![Screenshot from 2022-07-08 00-44-46.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657274648832/nMGac-IGE.png align="left")

**Step 2:-** To Write in this file you will have to first Press ` i` it then only let you write in this file it means now you are in an INSERT mode as you can see in the above image.

**Step 3:- ** Now if you have done your editing of the file you will like to SAVE and get EXIT from the VIM editor to do that you have to first press `ESC` then  Press `:wq`
> `:`- This will be used will be giving the commands.

> `w`- It stands for write.

> `q` - it stands for quit.

But what if you don't want to write anything and just want to read the file. In that case, you have to press `:q!` in this, and you will exit the file without making any changes.

These are some other commands that you can use while editing your file in the VIM editor

- hjkl : move the cursor around to left, down, up, and right respectively.
- 7j : move 7 lines down.
- w : move a word forward
- ctrl + f : move down a page
- ctrl + b : move up a page
- gg : move to the top of the document
- G : move to the bottomost of the document
- dw : delete a word
- d6w : delete 6 words
- dt> : delete till `>`
- di] : delete everything inside `[ ]`
- dd : delete whole line
- 4dd : delete 4 lines
- yy : yank a line ( yank is copy )
- cc : change a line ( change is delete and go in insert mode )
- cap : change a paragraph
- `.` : repeat last command
- f' : find first occurance of `'`
- f'ci'hello : _find the next `'` then change everything inside `'` for `hello`

The list goes on and on...