# vim-go-ide
It is a powerful and high efficiently golang IDE with these configuration.You can start to use in miniutes.

# Quick install
Make sure you have go and vim installed, and also specified GOPATH.Then follow the steps below:

1.  git clone https://github.com/imroc/vim-go-ide.git
2.  copy `.vimrc` to your home directory
3.  git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
4.  run `:PluginInstall` in your vim to download vim plugins
5.  run `:GoInstallBinaries` in your vim to install go tools used by vim-go,or just copy `bin/` to your `$GOPATH/` if you are in some country that blocked google's websites

Aha,that's all,pretty simple,isn't it?

If you want to update go tools used by vim-go,like godef,gocode,goimports etc,you could run `:GoUpdateBinaries` in vim.

# How to use
Note:We mapped key <leader> as "," and <esc> as "kj".All of the shortcut is in normal mode.

1.  Run current go package:`<leader>r` or `:GoRun`.
2.  Build current go package:`<leader>b` or `:GoBuild`.
3.  Test current go package:`<leader>t` or `:GoTest`.
4.  When error happens,quickfix list will be opened,`ctrl-n` or `:cnext` jump to next error,`ctrl-m` or `:cprevious` jump to previous error,`<leader>a` or `:cclose` close the quickfix list,`copen` open it again.
5.  To see the code where the test is covered or not:`<leader>c` or `:GoCoverageToggle`.You can also see it in browser:`:GoCoverageBrowser`.`:GoCoverage` and `:GoCoverageClear` can start and stop it respectively.
6.  `:GoImport` can import package,`:GoImportAs`can give it a alias name,`:GoDrop` can drop the import.
7.  "if" means "inner function","af" means "a function",including its' comments.depending on your cursor's place,`dif` delete a innser function,`daf` delete a whole function,`vif` select inner function,`vaf` select the whole function,`yif` copy the inner function,`yaf` copy the whole function.
8.  `gS` split the struct expression into multiple lines,`gJ` join it into one line.
9.  `:GoFmt` format your code,including import and error check,and when you save file,it will also do all the stuff.
10.  In insert mode,type `errp` and hit `tab`,comes out a err handle template:

```
if err != nil {
    panic( )
          ^
          cursor position
}
```

Similarly:

```
fn -> fmt.Println()
ff -> fmt.Printf()
ln -> log.Println()
lf -> log.Printf()
```

And if you are write a struct which related to json:

```
type foo struct {
    Message string .
                   ^ put your cursor here 
}
```

Just hit the tab,then came out a template:

```
type foo struct {
	Message  string `json:"message"`
}
```

11. `K`,`ctrl-]` or `:GoDef` go to definition,`ctrl-t` back to previous location where you invoked `:GoDef`.`:GoDefStack` to see history locations where invoked `:GoDef`,`:GoDefStackClear` to clear the stack list.
12. `:GoDecls` jumping between declarations in current file,while `:GoDeclsDir` is in current package.
13. `]]` jumping to next function,`[[` jumping to previous function,if you add number before them,for example,`3]]` jumping to third function based on current location.Similarly,`d]]` delete anything before next function,`v]]` select anything till the end of next function.
14. `:A` or `:Alternate` open test or source code coresponding to current go file in current window.`:AV` open it by splite window vertically,`:AS` is horizontally,`:AT` is open it in a new tab. 
15. `K` or `:GoDoc` to see documentation.
