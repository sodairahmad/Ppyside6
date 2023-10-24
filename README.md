# Ppyside6


from PySide6.QtWidgets import QWidget, QCheckBox,  QVBoxLayout,  QHBoxLayout, QGridLayout, QGroupBox, QButtonGroup, QRadioButton

#Radio Buttons, Check Boxes And Exclusive Check Boxes
class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Check Box and Radio Button")
        
        os = QGroupBox("Choose Operating Box")
        windows = QCheckBox("Windows")
        windows.toggled.connect(self.window_box_toggled)

        linux = QCheckBox("Linux")
        linux.toggled.connect(self.linux_box_toggled)

        mac = QCheckBox("Mac")
        mac.toggled.connect(self.mac_box_toggled)

        os_layout = QVBoxLayout()
        os_layout.addWidget(windows)
        os_layout.addWidget(linux)
        os_layout.addWidget(mac)

        os.setLayout(os_layout)

#Exclusive Check Boxes

        drinks = QGroupBox("Drinks layout")

        beer = QCheckBox("Beer")
        #beer.toggled.connect(self.window_box_toggled)
        juice = QCheckBox("Juice")
        #juice.toggled.connect(self.linux_box_toggled)
        coffee = QCheckBox("Coffee")
        #coffee.toggled.connect(self.mac_box_toggled)
        beer.setChecked(True)

        exclusive_button_group = QButtonGroup(self)
        exclusive_button_group.addButton(beer)
        exclusive_button_group.addButton(juice)
        exclusive_button_group.addButton(coffee)
        exclusive_button_group.setExclusive(True)

        drink_layout = QVBoxLayout()
        drink_layout.addWidget(beer)
        drink_layout.addWidget(juice)
        drink_layout.addWidget(coffee)
        drinks.setLayout(drink_layout)

#Radion Buttpon 
        answers = QGroupBox("Choose Answer:")
        a_answer = QRadioButton("A")
        b_answer = QRadioButton("B")
        C_answer = QRadioButton("c")
        d_answer = QRadioButton("D")

        v_layout = QVBoxLayout()
        v_layout.addWidget(a_answer)
        v_layout.addWidget(b_answer)
        v_layout.addWidget(C_answer)
        v_layout.addWidget(d_answer)
        a_answer.setChecked(True)
        answers.setLayout(v_layout)

        layout = QHBoxLayout()
        layout.addWidget(os)
        layout.addWidget(drinks)
        
        vert_layout = QVBoxLayout()
        vert_layout.addLayout(layout)
        vert_layout.addWidget(answers)

        self.setLayout(vert_layout)

    def window_box_toggled(self, checked):
        if checked:
            print("Windows checked:")
        else:
            print("Windows unchecked")

    def linux_box_toggled(self, checked):
        if checked:
            print("linux checked:")
        else:
            print("linux unchecked")

    def mac_box_toggled(self, checked):
        if checked:
            print("Mac checked:")
        else:
            print("Mac unchecked")

   #2...........................................
   #Button HOlder
   
from PySide6.QtGui import QAction, QIcon
from PySide6.QtCore import QSize
from PySide6.QtWidgets import QMenuBar, QApplication,  QToolBar, QWidget, QMainWindow, QPushButton, QStatusBar

class Widget(QMainWindow):
    def __init__(self, app):
        super().__init__()
        self.app = app
        self.setWindowTitle("Our Main Window")
        menu_bar = self.menuBar()

        file_menu = menu_bar.addMenu("File")
        quit_action = file_menu.addAction("Quit")
        open = file_menu.addAction("Open")
        open.triggered.connect(self.Open_text)
        closed = file_menu.addAction("Closed")
        closed.triggered.connect(self.tool_button_clicked)
        file_menu.addAction("Write")
        quit_action.triggered.connect(self.Quit_App)

        edit_menu = menu_bar.addMenu("Edit")
        edit = edit_menu.addAction("self.Delete")
        edit.triggered.connect(self.Delete)

        
        menu_bar.addMenu("Selection")
        menu_bar.addMenu("View")
        menu_bar.addMenu("Go")
        menu_bar.addMenu("Run")
        menu_bar.addMenu("Terminal")
        menu_bar.addMenu("Help")
        menu_bar.addMenu("Window")
        
        toolbar = QToolBar("Main tool Bar: ")
        toolbar.setIconSize(QSize(14, 13))
        self.addToolBar(toolbar)
        action1 = QAction("Quit App ", self)
        action1.setStatusTip("Action showment")
        action1.triggered.connect(self.tool_button_clicked)
        toolbar.addAction(action1)

        action2 = QAction("Closed App", self)
        action2.setStatusTip("Show Action")
        action2.triggered.connect(self.tool_button_clicked)
        toolbar.addAction(action2)

        toolbar.addSeparator()
        show = toolbar.addWidget(QPushButton("Click me"))
        show.triggered.connect(self.tool_button_clicked)
        self.setStatusBar(QStatusBar(self))



    def tool_button_clicked(self):
        self.statusBar().showMessage("The main window status bar")

    def Quit_App(self):
        self.app.quit()
    
    def Delete(self):
        self.delete.Quit_App
    def Open_text():
        ja = open('sodair.txt','+r')
        print(ja)

    (3)....................................
    #Grid layout

    from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QLineEdit, QSizePolicy, QGridLayout

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Grid Layout / Calculator Design")
        self.label = QLabel("Result: ")
        self.line_edit = QLineEdit(self)
        one = QPushButton("1")
        two = QPushButton("2")
        three = QPushButton("3")
        four = QPushButton("4")
        five = QPushButton("5")
        six = QPushButton("6")
        seven = QPushButton("7")
        eight = QPushButton("8")
        nine = QPushButton("9")
        zero = QPushButton("0")
        equal = QPushButton("=")
        clear = QPushButton("Clear")
        one.clicked.connect(lambda: self.Six("1"))
        two.clicked.connect(lambda: self.Six("2"))
        three.clicked.connect(lambda: self.Six("3"))
        four.clicked.connect(lambda: self.Six("4"))
        five.clicked.connect(lambda: self.Six("5"))
        
        #Symbols
        plus = QPushButton("+")
        minus = QPushButton("-")
        multiply = QPushButton("x")
        divide = QPushButton("/")
        back = QPushButton("Back")
        plus.clicked.connect(lambda: self.Six("+"))
        minus.clicked.connect(lambda: self.Six("-"))
        divide.clicked.connect(lambda: self.Six("/"))
        multiply.clicked.connect(lambda: self.Six("*"))
        equal.clicked.connect(lambda: self.Six("="))
        clear.clicked.connect(self.clear)
                              
    

        grid_layout = QGridLayout()
        grid_layout.addWidget(one, 0, 0)
        grid_layout.addWidget(two, 0,1)
        grid_layout.addWidget(three, 0,2)
        grid_layout.addWidget(four, 1,0)
        grid_layout.addWidget(five, 1,1)
        grid_layout.addWidget(six, 1,2)
        grid_layout.addWidget(seven, 2,0)
        grid_layout.addWidget(eight, 2,1)
        grid_layout.addWidget(nine, 2,2)
        grid_layout.addWidget(zero, 3,0, )
        grid_layout.addWidget(self.label, 3,1)
        grid_layout.addWidget(back, 3,2)
        grid_layout.addWidget(plus, 0,3)
        grid_layout.addWidget(minus, 1,3)
        grid_layout.addWidget(multiply, 2,3)
        grid_layout.addWidget(divide, 3,3)
        grid_layout.addWidget(self.line_edit, 4,0, 1,3)
        grid_layout.addWidget(equal, 4,2)
        grid_layout.addWidget(clear, 4,3)

        self.setLayout(grid_layout)

    def Six(self, text):
        action_text = self.line_edit.text()
        existing_text = action_text + "" + text 
        new = self.line_edit.setText(existing_text)
        ja = float(self.line_edit.text())
        print(ja)
    
    def clear(self):
        self.line_edit.clear()
    
    (4).............................................................
    #MessageBox 
    
from PySide6.QtWidgets import QVBoxLayout,  QWidget, QPushButton,  QMessageBox, QHBoxLayout
 

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Messange Box")

        buttonHard = QPushButton("hard")
        buttonHard.clicked.connect(self.button_hard_clicked)
        buttonCritical = QPushButton("critical")
        buttonCritical.clicked.connect(self.button_critical_clicked)
        buttonInformation = QPushButton("Information")
        buttonInformation.clicked.connect(self.button_information_clicked)
        buttonWarning = QPushButton("Warning")
        buttonWarning.clicked.connect(self.button_warning_clicked)
        buttonAbout = QPushButton("About")
        buttonAbout.clicked.connect(self.button_about_clicked)

        layout = QHBoxLayout()
        layout.addWidget(buttonHard)
        layout.addWidget(buttonCritical)
        layout.addWidget(buttonInformation)
        layout.addWidget(buttonWarning)
        layout.addWidget(buttonAbout)
        self.setLayout(layout)

    def button_hard_clicked(self):
        ret = QMessageBox.critical(self, "Message Box", "What do you want to do with this? ", QMessageBox.Ok | QMessageBox.Cancel)
        if ret == QMessageBox.Ok:
            print("You Clicked Ok")
        else:
            print("You Clicked cancel")

    def button_critical_clicked(self):
        ret = QMessageBox.question(self, "Message Box", "What do you want to do with this? ", QMessageBox.Ok | QMessageBox.Cancel)
        if ret == QMessageBox.Ok:
            print("You Clicked Ok")
        else:
            print("You Clicked cancel")
    
    def button_information_clicked(self):
        ret = QMessageBox.information(self, "Message Box", "What do you want to do with this? ", QMessageBox.Ok | QMessageBox.Cancel)
        if ret == QMessageBox.Ok:
            print("You Clicked Ok")
        else:
            print("You Clicked cancel")
    
    def button_warning_clicked(self):
        ret = QMessageBox.warning(self, "Message Box", "What do you want to do with this? ", QMessageBox.Ok | QMessageBox.Cancel)
        if ret == QMessageBox.Ok:
            print("You Clicked Ok")
        else:
            print("You Clicked cancel")
    
    def button_about_clicked(self):
        ret = QMessageBox.about(self, "Message Box", "Some About Message: ")
        if ret == QMessageBox.Ok:
            print("You Clicked Ok")
        else:
            print("You Clicked cancel")

(5)......................................
#Combo Box
from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QTabWidget, QComboBox

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Q ComboBox demu")

        self.combo_box = QComboBox(self)

        self.combo_box.addItem("Earth")
        self.combo_box.addItem("Venus")
        self.combo_box.addItem("Mars")
        self.combo_box.addItem("Pluton")
        self.combo_box.addItem("Saturn")
        self.combo_box.addItem("Unknown")

        current_value = QPushButton("Current Value")
        current_value.clicked.connect(self.current_value)
        set_current_value = QPushButton("Set Value")
        set_current_value.clicked.connect(self.set_current_value)
        get_value = QPushButton("Get Value")
        get_value.clicked.connect(self.get_value)

        vert_layout = QVBoxLayout()
        vert_layout.addWidget(self.combo_box)
        vert_layout.addWidget(current_value)
        vert_layout.addWidget(set_current_value)
        vert_layout.addWidget(get_value)

        self.setLayout(vert_layout)


    def current_value(self):
        print(f"current item: {self.combo_box.currentText()} having current index: {self.combo_box.currentIndex()}")

    def set_current_value(self):
        self.combo_box.setCurrentIndex(2)
    def get_value(self):
        for i in range(self.combo_box.count()):
            print(f"index {i} \, {self.combo_box.itemText(i)}")

(6)...............................................
#Qlabel Image

from PySide6.QtGui import QPixmap
from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QLineEdit 

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Qlabel Image:")

        image_label = QLabel()
        image_label.setPixmap(QPixmap("images/delete.png"))

        layout = QVBoxLayout()
        layout.addWidget(image_label)

        self.setLayout(layout)
(7).........................................
#Qlabel

from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QLineEdit 

class Widget(QWidget):
    def __init__(self):
        super().__init__()
        
        self.setWindowTitle("Qlabel and QlineEdit")

        label = QLabel("Full Name: ")
        self.line_edit = QLineEdit()
        self.line_edit.textChanged.connect(self.text_changed)
        self.line_edit.cursorPositionChanged.connect(self.cursor_position_changed)
        self.line_edit.editingFinished.connect(self.editing_finish)
        self.line_edit.returnPressed.connect(self.return_pressed)
        self.line_edit.selectionChanged.connect(self.selection_changed)
        self.line_edit.textEdited.connect(self.text_edited)

        button = QPushButton("Grab Data: ")
        button.clicked.connect(self.grab_data)
        self.text_holder_label = QLabel("I am Here: ")

        hh_layout = QHBoxLayout()
        hh_layout.addWidget(button)

        h_layout = QHBoxLayout()
        h_layout.addWidget(label)
        h_layout.addWidget(self.line_edit)
        
        

        v_layout = QVBoxLayout()
        v_layout.addLayout(h_layout)
        v_layout.addLayout(hh_layout)
        v_layout.addWidget(self.text_holder_label)
        self.setLayout(v_layout)
    
    def grab_data(self):
        print(f"Full Name: {self.line_edit.text()}")
        self.text_holder_label.setText(self.line_edit.text())

    def text_changed(self):
        self.text_holder_label.setText(self.line_edit.text())
    
    def cursor_position_changed(self, old, new):
        print("Cousor Old Position", old, "Cursor new Position: ", new)

    def editing_finish(self):
        print("Editing Finish Dear")

    def return_pressed(self):
        print("Return Pressed")

    def selection_changed(self):
        print(f"Selection Changed: {self.line_edit.selectedText()}")

    def text_edited(self, new_text):
        print(f"Edited text: ", new_text)
(8)............................................
#Qwidget

from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QListWidget, QAbstractItemView

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Q List Widget demu")

        self.set_listwidget = QListWidget(self)
        self.set_listwidget.setSelectionMode(QAbstractItemView.MultiSelection)
        self.set_listwidget.addItem("One")
        self.set_listwidget.addItems(["two", "Three"])
        self.set_listwidget.currentItemChanged.connect(self.current_item_changed)
        self.set_listwidget.currentTextChanged.connect(self.current_text_changed)

        add_button = QPushButton("Add Item")
        add_button.clicked.connect(self.add_item) 
        delete_button = QPushButton("Delete Item")
        delete_button.clicked.connect(self.delete_item)
        count_button = QPushButton("Count Item")
        count_button.clicked.connect(self.count_item)
        select_button = QPushButton("Select Item")
        add_button.clicked.connect(self.select_item)



        vet_layout = QVBoxLayout()
        vet_layout.addWidget(self.set_listwidget)
        vet_layout.addWidget(add_button)
        vet_layout.addWidget(delete_button)
        vet_layout.addWidget(count_button)
        vet_layout.addWidget(select_button)

        self.setLayout(vet_layout)

    def current_item_changed(self, item):
            print(f" Item: {item.text()}")

    def current_text_changed(self,text):
            print(f"Current Item: {text}")

    def add_item(self):
          self.set_listwidget.addItem(input("Add Items"))
          
    def delete_item(self):
          self.set_listwidget.takeItem(self.set_listwidget.currentRow())
        
    def count_item(self):
          print("Items Count: ", self.set_listwidget.count())

    def select_item(self):
          list = self.set_listwidget.selectedItems()
          for i in list:
                print(i.text())

(9)..................................................
#Qsize Policy


from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QLineEdit, QSizePolicy

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Size ploicy")

        label = QLabel("Some Text")
        line_edit = QLineEdit()
        label.setSizePolicy(QSizePolicy.Expanding, QSizePolicy.Fixed)

        h_layout = QHBoxLayout()
        h_layout.addWidget(label)
        h_layout.addWidget(line_edit)

        one = QPushButton("One")
        two = QPushButton("Two")
        three = QPushButton("Three")

        h1_layout = QHBoxLayout()
        h1_layout.addWidget(one,3)
        h1_layout.addWidget(two,2)
        h1_layout.addWidget(three,1)

        layout = QVBoxLayout()
        layout.addLayout(h_layout)
        layout.addLayout(h1_layout)
        self.setLayout(layout)

(10)..................................................
#QtabWidget

from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QLabel, QPushButton, QTabWidget, QLineEdit

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Q Tab Widget demu")

        tab_widget = QTabWidget(self)

        widget_form = QWidget()
        full_name_label = QLabel("Full Name")
        line_edit = QLineEdit()

        lay_out = QHBoxLayout()
        lay_out.addWidget(full_name_label)
        lay_out.addWidget(line_edit)

        widget_form.setLayout(lay_out)
        
    #Button Widget Creation 
        widget_button = QWidget()

        one_button = QPushButton("one")
        one_button.clicked.connect(self.button_one_clicked)
        two_button = QPushButton("two")
        two_button.clicked.connect(self.button_two_clicked)
        three_button = QPushButton("three")
        three_button.clicked.connect(self.button_three_clicked)

        v_layout = QVBoxLayout()
        v_layout.addWidget(one_button)
        v_layout.addWidget(two_button)
        v_layout.addWidget(three_button)
        widget_button.setLayout(v_layout)

    #Second Button Widget

        widget2_button = QWidget()

        one_button = QPushButton("four")
        one_button.clicked.connect(self.button_four_clicked)
        two_button = QPushButton("five")
        two_button.clicked.connect(self.button_five_clicked)
        three_button = QPushButton("six")
        three_button.clicked.connect(self.button_six_clicked)

        v_layout = QVBoxLayout()
        v_layout.addWidget(one_button)
        v_layout.addWidget(two_button)
        v_layout.addWidget(three_button)
        widget2_button.setLayout(v_layout)


        tab_widget.addTab(widget_form,"Information")
        tab_widget.addTab(widget_button, "Buttons")
        tab_widget.addTab(widget2_button,"2nd Button")

        ver_layout = QVBoxLayout()
        ver_layout.addWidget(tab_widget)
        self.setLayout(ver_layout)


    def button_one_clicked(self):
        print("Button one clicked")
    
    def button_two_clicked(self):
        print("Button two clicked")

    def button_three_clicked(self):
        print("Button three clicked")
    def button_four_clicked(self):
        print("Button four clicked")
    
    def button_five_clicked(self):
        print("Button five clicked")

    def button_six_clicked(self):
        print("Button six clicked")

(11).....................................................
#Text Editor
from PySide6.QtWidgets import QWidget, QVBoxLayout, QHBoxLayout, QTextEdit, QPushButton, QLineEdit 

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("QTextEdit Demu:")

        self.text_edit = QTextEdit()

        current_text_button = QPushButton("Current Text")
        current_text_button.clicked.connect(self.current_text_button_clicked)

        copy_button = QPushButton("Copy")
        copy_button.clicked.connect(self.text_edit.copy)

        cut_button = QPushButton("Cut")
        cut_button.clicked.connect(self.text_edit.cut)

        paste_button = QPushButton("Paste")
        paste_button.clicked.connect(self.text_edit.paste)

        undo_button = QPushButton("Undo")
        undo_button.clicked.connect(self.text_edit.undo)

        redo_button = QPushButton("Redo")
        redo_button.clicked.connect(self.text_edit.redo)

        plain_text_button = QPushButton("plain Text button")
        plain_text_button.clicked.connect(self.set_plan_text)

        html_button = QPushButton("Html")
        html_button.clicked.connect(self.set_html)

        clear_button = QPushButton("Clear")
        clear_button.clicked.connect(self.text_edit.clear)


        layout = QHBoxLayout()
        layout.addWidget(current_text_button)
        layout.addWidget(copy_button)
        layout.addWidget(cut_button)
        layout.addWidget(paste_button)
        layout.addWidget(undo_button)
        layout.addWidget(redo_button)
        layout.addWidget(plain_text_button)
        layout.addWidget(html_button)
        layout.addWidget(clear_button)

        v_layout = QVBoxLayout()
        v_layout.addLayout(layout)
        v_layout.addWidget(self.text_edit)

        self.setLayout(v_layout)

    def current_text_button_clicked(self):
        print(self.text_edit.toPlainText())

    def set_plan_text(self):
        (self.text_edit.setPlainText)
    
    def set_html(self):
        (self.text_edit.setHtml)
(12).................................................
#QWidget
from PySide6.QtWidgets import QVBoxLayout,  QWidget, QPushButton,  QMessageBox, QHBoxLayout
 

class Widget(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Our Main Window:")

        
        button = QPushButton("Click")
        button.clicked.connect(self.button_clicked)
        button.pressed.connect(self.button_pressed)
        button.released.connect(self.button_released)
        

        layout = QVBoxLayout()
        layout.addWidget(button)
        self.setLayout(layout)

    def button_clicked(self):
        print("clicked")

    def button_pressed(self):
        print("Pressed")

    def button_released(self):
        print("Released")
    
