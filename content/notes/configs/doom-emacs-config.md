---
title: "Literate Emacs Configuration"
author: ["Aidan Scannell"]
draft: false
type: "book"
---

My personal [doom emacs](https://github.com/doomemacs/doomemacs) literate configuration.


## Doom Configurations {#doom-configurations}


### Doom config options {#doom-config-options}

```emacs-lisp
;; Whenever you reconfigure a package, make sure to wrap your config in an
;; `after!' block, otherwise Doom's defaults may override your settings. E.g.

;;   (after! PACKAGE
;;     (setq x y))

;; The exceptions to this rule:

;;   - Setting file/directory variables (like `org-directory')
;;   - Setting variables which explicitly tell you to set them before their
;;     package is loaded (see 'C-h v VARIABLE' to look up their documentation).
;;   - Setting doom variables (which start with 'doom-' or '+').

;; Here are some additional functions/macros that will help you configure Doom.

;; - `load!' for loading external *.el files relative to this one
;; - `use-package!' for configuring packages
;; - `after!' for running code after a package has loaded
;; - `add-load-path!' for adding directories to the `load-path', relative to
;;   this file. Emacs searches the `load-path' when you load packages with
;;   `require' or `use-package'.
;; - `map!' for binding new keys

;; To get information about any of these functions/macros, move the cursor over
;; the highlighted symbol at press 'K' (non-evil users must press 'C-c c k').
;; This will open documentation for it, including demos of how they are used.
;; Alternatively, use `C-h o' to look up a symbol (functions, variables, faces,
;; etc).

;; You can also try 'gd' (or 'C-c c d') to jump to their definition and see how
;; they are implemented.
```


### Personal Info {#personal-info}

Some functionality uses this to identify you, e.g. GPG configuration, email
clients, file templates and snippets. It is optional.

```emacs-lisp
(setq user-full-name "Aidan Scannell"
      user-mail-address "scannell.aidan@gmail.com")
```


### Fonts {#fonts}

Doom exposes five (optional) variables for controlling fonts in Doom:

-   \`doom-font' -- the primary font to use
-   \`doom-variable-pitch-font' -- a non-monospace font (where applicable)
-   \`doom-big-font' -- used for \`doom-big-font-mode'; use this for
    presentations or streaming.
-   \`doom-unicode-font' -- for unicode glyphs
-   \`doom-serif-font' -- for the \`fixed-pitch-serif' face

See 'C-h v doom-font' for documentation and more examples of what they
accept. For example:

```emacs-lisp
;; (setq doom-font (font-spec :family "Fira Code" :size 12 :weight 'semi-light)
;;      doom-variable-pitch-font (font-spec :family "Fira Sans" :size 13))
```

If you or Emacs can't find your font, use 'M-x describe-font' to look them
up, \`M-x eval-region' to execute elisp code, and 'M-x doom/reload-font' to
refresh your font settings. If Emacs still can't find your font, it likely
wasn't installed correctly. Font issues are rarely Doom issues!


### Theme {#theme}

There are two ways to load a theme. Both assume the theme is installed and
available. You can either set \`doom-theme' or manually load a theme with the
\`load-theme' function. This is the default:

```emacs-lisp
;; (setq doom-theme 'doom-one)
;; (setq doom-theme 'doom-dracula)
(setq doom-theme 'doom-laserwave)
;; (setq doom-theme 'doom-moonlight)
;; (setq doom-theme 'doom-monokai)
;; (setq doom-theme 'doom-wilmersdorf)
```


### Line numbers {#line-numbers}

This determines the style of line numbers in effect. If set to \`nil', line
numbers are disabled. For relative line numbers, set this to \`relative'.

```emacs-lisp
(setq display-line-numbers-type t)
```


### Set org-directory {#set-org-directory}

If you use \`org' and don't want your org files in the default location below,
change \`org-directory'. It must be set before org loads!

```emacs-lisp
(setq org-directory (concat (getenv "HOME")"/Library/Mobile Documents/com~apple~CloudDocs/org"))
;; (setq org-directory "~/Dropbox/org")
```


## Custom Configurations {#custom-configurations}


### Set variables {#set-variables}

```emacs-lisp
(setq zot_bib (concat org-directory "/ref/zotero-library.bib")
      ;; org_ref_bib (concat (getenv "HOME") "/Dropbox/org/ref/org-ref-library.bib")
      org_notes org-directory
      org_contacts (concat org-directory "/contacts.org"))
```


### Org mode {#org-mode}


#### org-projectile {#org-projectile}

```emacs-lisp
(package! org-projectile)
```

```emacs-lisp
(after! org
  (use-package! org-projectile
    :config
    (org-projectile-per-project)
    (setq org-projectile-per-project-filepath "todo.org")
    (setq org-agenda-files (append org-agenda-files (org-projectile-todo-files)))
    ;; (setq org-projectile-projects-file "~/Dropbox/org/project_todos.org")
    (setq org-projectile-projects-file "~/Library/Mobile Documents/com~apple~CloudDocs/org/project_todos.org")
    (push (org-projectile-project-todo-entry) org-capture-templates)
    ;; (global-set-key (kbd "C-c c") 'org-capture)
    ;; (global-set-key (kbd "C-c n p") 'org-projectile-project-todo-completing-read)))
    ;; :init
    ;; (org-projectile-per-project)
    ;; (setq org-projectile-per-project-filepath "project_todos.org")
    ;; (setq org-agenda-files (append org-agenda-files (org-projectile-todo-files)))
    ;; (setq org-projectile-projects-file "~/Dropbox/org/project_todos.org")
    ;; (setq org-agenda-files (append org-agenda-files (org-projectile-todo-files)))
    ;; (push (org-projectile-project-todo-entry) org-capture-templates)
    ;; (global-set-key (kbd "C-c c") 'org-capture)
    ;; (global-set-key (kbd "C-c n p") 'org-projectile-project-todo-completing-read)))

    (setq org-contacts-files org_contacts
          org-todo-keywords '((sequence "SOMEDAY" "TODO" "PROGRESS" "|" "DONE" "DELEGATED" "CANCELLED"))
          ;;  ;; org-default-notes-file "~/Dropbox/org/notes.org"
          org-startup-indented t ;; Keep the indentation well structured
          org-bullets-bullet-list '("■" "◆" "▲" "▶"))))
```


#### org ref {#org-ref}

```emacs-lisp
(package! org-ref)
```

I now use doom's biblio module for working with bibliographies and citations.
However, I still need org-ref for cross referencing within org files e.g. <fig-cat>.

```emacs-lisp
(use-package! org-ref)
;; (after! org
;;     (use-package! org-ref
;;       :config
;;       (setq org-ref-default-bibliography zot_bib)))
```


#### biblio module config {#biblio-module-config}

Setup citar to use zotero bib file in cloud

```emacs-lisp
(use-package! citar
  :config
  (setq! citar-bibliography zot_bib))
```

Set citar notes/files directories using org-roam

```emacs-lisp
;; (setq! citar-library-paths '("/path/to/library/files/")
```

Make citar use all-the-icons symbols.

```emacs-lisp
;; (setq citar-symbols
;;       `((file ,(all-the-icons-faicon "file-o" :face 'all-the-icons-green :v-adjust -0.1) . " ")
;;         (note ,(all-the-icons-material "speaker_notes" :face 'all-the-icons-blue :v-adjust -0.3) . " ")
;;         (link ,(all-the-icons-octicon "link" :face 'all-the-icons-orange :v-adjust 0.01) . " ")))
(setq citar-symbol-separator "  ")
```

Use org-roam-bibtex to link org-roam notes to bibtex entries.

```emacs-lisp
(package! org-roam-bibtex
  :recipe (:host github :repo "org-roam/org-roam-bibtex"))

;; When using org-roam via the `+roam` flag
(unpin! org-roam)
```

```emacs-lisp
(use-package! org-roam-bibtex
  :after org-roam
  :config
  (require 'org-roam-bibtex)
  ;; (setq org-roam-capture-templates
  ;;       '(;; ... other templates
  ;;         ;; bibliography note template
  ;;         ("r" "bibliography reference" plain "%?"
  ;;          :target
  ;;          (file+head "references/${citekey}.org" "#+title: ${title}\n")
  ;;          :unnarrowed t)))

  ;; TODO update these templates to use my org roam files
  ;; (setq org-roam-capture-templates
  ;; '(
  ;;   ;; ("d" "default" plain "%?"
  ;;   ;;  :if-new (file+head "${slug}.org"
  ;;   ;;                     "#+title: ${title}\n#+SETUPFILE: ~/bib-lib/setup_file.org\n* References :ignore:\n#+print_bibliography:")
  ;;   ;;  :unnarrowed t)
  ;;   ;; capture to inbox
  ;;   ("i" "inbox" entry "* TODO %?\n"
  ;;    :target (node "45acaadd-02fb-4b93-a741-45d37ff9fd5e")
  ;;    :unnarrowed t
  ;;    :empty-lines-before 1
  ;;    :empty-lines-after 1
  ;;    :prepend t)
  ;;   ;; bibliography note template
  ;;   ("r" "bibliography reference" plain "%?"
  ;;    :if-new (file+head "references/notes_${citekey}.org"
  ;;                       "#+title: Notes on ${title}\n#+SETUPFILE: ~/bib-lib/ref_setup_file.org\n* References :ignore:\n#+print_bibliography:")
  ;;    :unnarrowed t)
  ;;   ;; for my annotated bibliography needs
  ;;   ("s" "short bibliography reference (no id)" entry "* ${title} [cite:@%^{citekey}]\n%?"
  ;;    :target (node "01af7246-1b2e-42a5-b8e7-68be9157241d")
  ;;    :unnarrowed t
  ;;    :empty-lines-before 1
  ;;    :prepend t)))

  (setq citar-notes-paths (list (concat org-directory "/roam/references")
                                org-roam-directory (concat org-directory "/roam"))
        ))
;; (use-package! org-roam-bibtex
;; :config

;; (defun robo/capture-to-inbox ()
;;   "Capture a TODO straight to the inbox."
;;   (interactive)
;;   (org-roam-capture- :goto nil
;;                      :keys "i"
;;                      :node (org-roam-node-from-id "45acaadd-02fb-4b93-a741-45d37ff9fd5e")))
;; (setq citar-open-note-function 'orb-citar-edit-note
;;       citar-notes-paths (concat org-directory "/roam/references")
;;       orb-preformat-keywords '("citekey" "title" "url" "author-or-editor" "keywords" "file")
;;       orb-process-file-keyword t
;;       orb-file-field-extensions '("pdf")))
```


#### Set up ignore headings tag {#set-up-ignore-headings-tag}

Import ignore-headlines to allow a headline (but not its children) to
be ignored.  Any headline tagged with the 'ignore' tag will be
ignored (i.e. will not be included in the export), but any child
headlines will not be ignored (unless explicitly tagged to be
ignored), and will instead have their levels promoted by one.

```emacs-lisp
(package! org-contrib)
```

```emacs-lisp
(after! org
    (use-package! org-contrib
      :config
      (require 'ox-extra)
      (ox-extras-activate '(latex-header-blocks ignore-headlines))))
    ;; (use-package! ox-extra
    ;;   :config
    ;;   (ox-extras-activate '(latex-header-blocks ignore-headlines)))
```


#### org latex {#org-latex}

```emacs-lisp
(after! org
    (use-package! ox-latex
      :config
      (setq org-latex-pdf-process
            ;; '("latexmk -interaction=nonstopmode -output-directory=./tex -output-format=pdf %f"))))
            '("mkdir compile \n latexmk -cd -f -interaction=nonstopmode -outdir=./compile -auxdir=./compile -output-format=pdf %f \n cp ./compile/%b.pdf ./%b.pdf"))))
      ;; '("latexmk -f -silent -output-directory=./tex -output-format=pdf %f \n cp ./tex/%b.pdf ./%b.pdf"))
      ;; (setq org-latex-with-hyperref nil) ;; stop org adding hypersetup{author..} to latex export
      ;; (setq org-latex-prefer-user-labels t)
```


#### org-babel {#org-babel}

```emacs-lisp
(org-babel-do-load-languages
 'org-babel-load-languages
 '((python . t)
   (ipython . t)
   (elisp . t)
   (latex . t)
   (org . t)))
```


#### org-roamv2 {#org-roamv2}

```emacs-lisp

```


### Format {#format}

Disable formatter from lsp so that (format +onsave)

```emacs-lisp
;; (setq +format-with-lsp nil)
```

```emacs-lisp
;; (setq-hook! 'python-mode-hook +format-with 'html-tidy)
;; (setq-hook! 'python-mode-hook +format-with :none)
```

```emacs-lisp
(defvar +format-on-save-enabled-modes
  '(not emacs-lisp-mode    ; elisp's mechanisms are good enough
        sql-mode           ; sqlformat is currently broken
        tex-mode           ; latexindent is broken
        latex-mode
        html-mode
        org-msg-edit-mode) ; doesn't need a formatter
  )
```


### Spacemacs Keybindings {#spacemacs-keybindings}

Change meta to use SPC like spacemacs

```emacs-lisp
(map! :leader
      (:desc "M-x" "SPC"  #'execute-extended-command)
      (:desc "M-x" "C-SPC"  #'execute-extended-command))
```

avy jump like spacemacs

```emacs-lisp
(after! avy
  (map! :leader
        (:prefix-map ("j" . "jump")
         :desc "jump to char" "j"  #'avy-goto-char-2
         :desc "jump to word" "w"  #'avy-goto-word-0
         :desc "jump to line" "l"  #'avy-goto-line
         :desc "jump to url" "u"   #'avy-goto-url
         :desc "imenu" "i"  #'counsel-imenu
         :desc "switch-buffer" "b"  #'+ivy/switch-workspace-buffer
         :desc "goto-last-change" "c"  #'goto-last-change
         :desc "find-function" "f"  #'find-function
         :desc "find-variable" "v"  #'find-variable
         )))
```

Comment lines with SPC ;;

```emacs-lisp
(map! :after evil
      :leader
      :desc "comment lines" ";" 'evilnc-comment-or-uncomment-lines)
```

Deleted other window using SPC w D

```emacs-lisp
(map! :map evil-window-map
      :desc "delete other window" "D" #'ace-delete-window)
```

Change workspaces to "layouts" using l instead of using TAB

```emacs-lisp
(map! :leader
      (:prefix-map ("l" . "layouts")
       :desc "previos" "k"  #'+workspace/switch-left
       :desc "next" "j"  #'+workspace/switch-right
       :desc "switch" "l"  #'+workspace/switch-to
       :desc "delete" "d"  #'+workspace/delete
       :desc "new" "n"  #'+workspace/new
       ))
```


### Dired {#dired}

```emacs-lisp
;; TODO update these to not use dropbox
;; dired quick links
(defun my/open-config () (interactive) (dired "/Users/scannea1/.config"))
(defun my/open-dotfiles() (interactive) (dired "/Users/scannea1/.dotfiles"))
;; (defun my/open-python-projects () (interactive) (dired "/Users/scannea1/Developer/python-projects"))
(defun my/open-python-projects () (interactive) (dired "/Users/scannea1/python-projects"))
(defun my/open-home () (interactive) (dired "/Users/scannea1"))
(defun my/open-documents () (interactive) (dired "/Users/scannea1/Documents"))
(defun my/open-emacs () (interactive) (dired doom-private-dir))
;; (defun my/open-downloads () (interactive) (dired "/Users/scannea1/Downloads"))
(defun my/open-org-directory() (interactive) (dired org-directory))
(defun my/open-notes () (interactive) (dired "/Users/scannea1/Dropbox/org"))

(map! :after dired
      :map dired-mode-map
      :ng "h" #'dired-up-directory
      :ng "l" #'dired-find-file)

(map! :after dired
      :leader
      (:prefix-map ("d" . "dired")
       :desc "~/.dotfiles" "c"  #'my/open-config
       :desc "~/dotfiles" "g"  #'my/open-dotfiles
       :desc "here" "d"  #'dired-jump
       :desc "emacs" "e"  #'my/open-emacs
       :desc "~/Documents" "D"  #'my/open-documents
       :desc "~/" "h"  #'my/open-home
       ;; :desc "~/Downloads" "o"  #'my/open-downloads
       :desc "org-directory" "o"  #'my/open-org-directory
       :desc "python-projects" "p"  #'my/open-python-projects
       :desc "notes" "n"  #'my/open-notes
       ))

(after! evil
  (after! dired-ranger
    (evil-collection-define-key 'normal 'dired-mode-map
      ;; "h" 'dired-single-up-directory
      "H" 'dired-omit-mode
      ;; "l" 'dired-single-buffer
      "y" 'dired-ranger-copy
      "X" 'dired-ranger-move
      "p" 'dired-ranger-paste)))
```

Change ls to gls for grouping by directories on osx

```emacs-lisp
;; (setq insert-directory-program "gls" dired-use-ls-dired t)
```

Make dired list directories first

```emacs-lisp
(setq dired-listing-switches "-agho --group-directories-first")
```

Make dired-omit-mode hide dotfiles

```emacs-lisp
(setq dired-omit-files "^\\.[^.].*")
```

```emacs-lisp
;; (setq dired-omit-verbose nil)
```

Dired preview for auto previewing files in dired.

```emacs-lisp
(package! dired-preview)
```

```emacs-lisp
;; (setq dired-omit-verbose nil)
(after! 'dired-preview

    ;; Default values for demo purposes
    (setq dired-preview-delay 0.2)
    (setq dired-preview-max-size (expt 2 100))
    (setq dired-preview-ignored-extensions-regexp
        (concat "\\."
                "\\(mkv\\|webm\\|mp4\\|mp3\\|ogg\\|m4a"
                "\\|gz\\|zst\\|tar\\|xz\\|rar\\|zip"
                "\\|iso\\|epub\\)"))
                ;; "\\|iso\\|epub\\|pdf\\)"))

    ;; Enable `dired-preview-mode' in a given Dired buffer or do it
    ;; globally:
    (dired-preview-global-mode 1)
)
```


### LaTeX {#latex}

```emacs-lisp
;; (add-hook pdf-view-mode-hook 'auto-revert-mode) # TODO add this back when pdf-tool is installed properly??
(add-hook 'TeX-after-compilation-finished-functions #'TeX-revert-document-buffer)

;; Config for doom latex lang
(after! reftex
  (setq reftex-default-bibliography zot_bib))

(setq +latex-viewers '(pdf-tools preview))
;; (setq +latex-viewers '(pdf-tools preview))
```


### Email {#email}

```emacs-lisp
;; (add-to-list 'load-path "~/Homebrew/bin/mu")
(setq mu4e-mu-binary "~/Homebrew/bin/mu")
```

Use mbsync for email.

```emacs-lisp
;; (setq +notmuch-sync-backend 'mbsync)
;; (setq +mu4e-backend 'offlineimap)

(set-email-account! "gmail"
  '((mu4e-sent-folder       . "/Sent Mail")
    (mu4e-drafts-folder     . "/Drafts")
    (mu4e-trash-folder      . "/Trash")
    (mu4e-refile-folder     . "/All Mail")
    (smtpmail-smtp-user     . "scannell.aidan@gmail.com")
    ;; (user-mail-address      . ".com")    ;; only needed for mu < 1.4
    (mu4e-compose-signature . "---\nYours truly\nThe Baz"))
  t)

(setq +mu4e-gmail-accounts '(("scannell.aidan@gmail.com" . "/scannell.aidan")))
;;                              ;; ("example@example.com" . "/example")))

(setq mu4e-context-policy 'ask-if-none
      mu4e-compose-context-policy 'always-ask)
```


#### mu4e-alert {#mu4e-alert}

This provides notifications through the [alert](https://github.com/jwiegley/alert) library.

If you don't like this use:

```emacs-lisp
;; add to $DOOMDIR/packages.el
;; (package! mu4e-alert :disable t)
```


#### Enabling automatic email fetching {#enabling-automatic-email-fetching}

By default, periodic email update is **disabled**. To enable periodic
mail retrieval/indexing, change the value of `mu4e-update-interval`:

```emacs-lisp
;; (setq mu4e-update-interval 60)
```


#### HMTL view with xwidgets {#hmtl-view-with-xwidgets}

```emacs-lisp
(package! mu4e-views)
```

```emacs-lisp
(add-to-list 'mu4e-headers-actions
             '("xWidget" . mu4e-action-view-with-xwidget) t)
(add-to-list 'mu4e-view-actions
             '("xWidget" . mu4e-action-view-with-xwidget) t)
```


### grip mode - view markdown/org in html {#grip-mode-view-markdown-org-in-html}

```emacs-lisp
(package! grip-mode)
```

```emacs-lisp
(after! grip-mode
  :ensure t
  :bind (:map markdown-mode-command-map
         ("g" . grip-mode)))

;; ;; Or using hooks
;; (package! grip-mode
;;   :ensure t
;;   :hook ((markdown-mode org-mode) . grip-mode))
```


### Elfeed for arxiv {#elfeed-for-arxiv}

Config feeds

```emacs-lisp
(setq elfeed-feeds
    '("http://export.arxiv.org/api/query?search_query=cat:stat.ML&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"
    "http://export.arxiv.org/api/query?search_query=cat:cs.LG&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"
    "http://export.arxiv.org/api/query?search_query=cat:cs.CL&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"))
;; (after! elfeed
;;     (setq elfeed-search-filter "@1-month-ago +unread")
;;     (setq elfeed-feeds
;;     '("http://export.arxiv.org/api/query?search_query=cat:stat.ML&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"
;;     "http://export.arxiv.org/api/query?search_query=cat:cs.LG&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"
;;     "http://export.arxiv.org/api/query?search_query=cat:cs.CL&start=0&max_results=100&sortBy=submittedDate&sortOrder=descending"))
;;     )
;; (setq elfeed-feeds
;;       '("https://this-week-in-rust.org/rss.xml"
;; 	"http://feeds.bbci.co.uk/news/rss.xml"))
;; (setq elfeed-feeds
;;       '("https://this-week-in-rust.org/rss.xml"
;;         "http://feeds.bbci.co.uk/news/rss.xml"))
```

Fetch papers whenever I open elfeed

```emacs-lisp
(add-hook! 'elfeed-search-mode-hook #'elfeed-update)
```
