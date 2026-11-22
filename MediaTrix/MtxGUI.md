## MtxGUI
MtxGui is meant to be a simple-to-use set of GUI objects. For that reason, this may look similar to HTML.

All classes below include `location` (X and Y for top-left) and `size` (X and Y again) as arguments.

* `MtxGUI.Window`
    * Arguments
        * scalable (Boolean): whether or not it can be scaled
    * Methods
        * `new_child_window`: makes a child window, same arguments except `parent_interact` (Boolean), which decides whether or not you can interact with the parent window