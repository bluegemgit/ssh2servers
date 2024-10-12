# 导入必要的库和模块
import tkinter as tk
from tkinter import ttk
from tkinter import scrolledtext
from tkinter import Menu
from tkinter import Spinbox
from tkinter import messagebox as mBox
 
# 自定义ToolTip类，用于为控件添加悬浮提示功能  
class ToolTip(object):  
    def __init__(self, widget):  
        # 初始化函数，传入需要添加提示的控件  
        self.widget = widget  
        self.tipwindow = None  
        self.id = None  
        self.x = self.y = 0  
 
    def showtip(self, text):  
        # 显示提示信息的函数  
        self.text = text  
        # 如果tipwindow已经存在或没有文本，则直接返回  
        if self.tipwindow or not self.text:  
            return  
        # 获取控件的位置信息，用于定位提示窗口  
        x, y, _cx, cy = self.widget.bbox("insert")  
        x = x + self.widget.winfo_rootx() + 27  
        y = y + cy + self.widget.winfo_rooty() + 27  
        # 创建一个Toplevel窗口作为提示窗口  
        self.tipwindow = tw = tk.Toplevel(self.widget)  
        tw.wm_overrideredirect(1)  # 去掉窗口的边框和标题栏  
        tw.wm_geometry("+%d+%d" % (x, y))  # 设置窗口位置  
  
        # 在提示窗口中添加一个Label用于显示文本  
        label = tk.Label(tw, text=self.text, justify=tk.LEFT,  
                         background="#ffffe0", relief=tk.SOLID, borderwidth=1,  
                         font=("tahoma", "8", "normal"))  
        label.pack(ipadx=1)  # 调整内部间距  
 
    def hidetip(self):  
        # 隐藏提示窗口的函数  
        tw = self.tipwindow  
        self.tipwindow = None  
        if tw:  
            tw.destroy()  # 销毁提示窗口  
       


       
# 定义一个函数，用于为指定的widget创建工具提示  
def createToolTip(widget, text):  
    # 创建一个ToolTip对象，与指定的widget相关联  
    toolTip = ToolTip(widget)  
    # 定义一个内部函数，当鼠标进入widget时调用，用于显示工具提示  
    def enter(event):  
        toolTip.showtip(text)  # 显示工具提示，并设置其文本为传入的text  
    # 定义一个内部函数，当鼠标离开widget时调用，用于隐藏工具提示  
    def leave(event):  
        toolTip.hidetip()  # 隐藏工具提示  
    # 绑定鼠标进入事件到enter函数，当鼠标进入widget时触发  
    widget.bind('<Enter>', enter)  
    # 绑定鼠标离开事件到leave函数，当鼠标离开widget时触发  
    widget.bind('<Leave>', leave)
    
    
    
    
# 创建实例  
win = tk.Tk()  # 创建一个Tk根窗口实例  
  
# 添加标题  
win.title("TTK 模板")  # 设置窗口标题为"Python 图形用户界面"  
  
# 禁用GUI的大小调整  
win.resizable(0,0)  # 设置窗口不可调整大小  
    
# 创建标签页控制器  
tabControl = ttk.Notebook(win)  # 在win窗口中创建一个Notebook（标签页控制器）  
  
# 创建第一个标签页  
tab1 = ttk.Frame(tabControl)  # 创建一个Frame作为第一个标签页的内容  
tabControl.add(tab1, text='第1页')  # 将tab1添加到标签页控制器中，并设置标签为"第1页"  
  
# 创建第二个标签页  
tab2 = ttk.Frame(tabControl)  # 创建一个Frame作为第二个标签页的内容  
tabControl.add(tab2, text='第2页')  # 将tab2添加到标签页控制器中，并设置标签为"第2页"  
  
# 创建第三个标签页  
tab3 = ttk.Frame(tabControl)  # 创建一个Frame作为第三个标签页的内容  
tabControl.add(tab3, text='第3页')  # 将tab3添加到标签页控制器中，并设置标签为"第3页"  
  
# 打包标签页控制器，使其可见并填充整个窗口  
tabControl.pack(expand=1, fill="both")  # 使用pack布局管理器，使标签页控制器扩展填满父容器win 

 
 
 # 创建一个ttk.LabelFrame控件，作为tab1上的一个容器，标题为'控件示范区1'  
monty = ttk.LabelFrame(tab1, text='控件示范区1')  
# 使用grid布局管理器放置LabelFrame，设置列、行、水平内边距和垂直内边距  
monty.grid(column=0, row=0, padx=8, pady=4)  
  
# 定义一个函数，当按钮被点击时执行  
def clickMe():  
    # 更新按钮的文本，包含输入框中的内容  
    action.configure(text='Hello\n ' + name.get())  
    # 禁用按钮，使其不可再点击  
    action.configure(state='disabled')  
  
# 在monty容器内创建一个标签，文本为"输入文字:"  
ttk.Label(monty, text="输入文字:").grid(column=0, row=0, sticky='W')  
  
# 创建一个StringVar对象，用于存储输入框中的文本  
name = tk.StringVar()  
# 创建一个输入框，绑定到name变量，放置在monty内  
nameEntered = ttk.Entry(monty, width=12, textvariable=name)  
nameEntered.grid(column=0, row=1, sticky='W')  
  
# 创建一个按钮，文本为"点击之后\n按钮失效"，点击时调用clickMe函数  
action = ttk.Button(monty, text="点击之后\n按钮失效", width=10, command=clickMe)  
# 使用grid布局管理器放置按钮，设置列、行、跨行数和内部垂直填充  
action.grid(column=2, row=1, rowspan=2, ipady=7)  
  
# 在monty容器内创建一个标签，文本为"请选择一本书:"  
ttk.Label(monty, text="请选择一本书:").grid(column=1, row=0, sticky='W')  
  
# 创建一个StringVar对象，用于存储下拉框中选中的值  
book = tk.StringVar()  
# 创建一个下拉框，绑定到book变量，放置在monty内，并设置可选值  
bookChosen = ttk.Combobox(monty, width=12, textvariable=book)  
bookChosen['values'] = ('平凡的世界', '亲爱的安德烈', '看见', '白夜行')  
# 放置下拉框，设置列和行  
bookChosen.grid(column=1, row=1)  
# 设置下拉框的初始选中项  
bookChosen.current(0)  
# 将下拉框设置为只读状态，不可编辑  
bookChosen.config(state='readonly')  
  
# 定义一个函数，当第一个Spinbox的值改变时执行  
def _spin():  
    # 获取Spinbox的值，并将其插入到滚动文本框中  
    value = spin.get()  
    scr.insert(tk.INSERT, value + '\n')  
  
# 定义一个函数，当第二个Spinbox的值改变时执行  
def _spin2():  
    # 获取Spinbox的值，并将其插入到滚动文本框中  
    value = spin2.get()  
    scr.insert(tk.INSERT, value + '\n')  
  
# 创建一个数值型的Spinbox，设置范围、宽度、边框宽度和命令函数  
spin = Spinbox(monty, from_=10, to=25, width=5, bd=8, command=_spin)  
# 放置Spinbox，设置列和行  
spin.grid(column=0, row=2)  
  
# 创建一个字符串型的Spinbox，设置可选值、宽度、边框宽度和命令函数  
spin2 = Spinbox(monty, values=('Python3入门', 'C语言', 'C++', 'Java', 'OpenCV'), width=13, bd=3, command=_spin2)  
# 放置Spinbox，设置列、行和文本对齐方式  
spin2.grid(column=1, row=2, sticky='W')  
  
# 创建一个滚动文本框，设置宽度、高度和文本换行方式  
scrolW, scrolH = 30, 5  
scr = scrolledtext.ScrolledText(monty, width=scrolW, height=scrolH, wrap=tk.WORD)  
# 放置滚动文本框，设置列、行、填充方式和跨列数  
scr.grid(column=0, row=3, sticky='WE', columnspan=3)  
  
# 假设createToolTip是一个自定义函数，用于为控件创建工具提示（此处未定义）  
createToolTip(spin, '这是一个Spinbox.')  
createToolTip(spin2, '这是一个Spinbox.')  
createToolTip(action, '这是一个Button.')  
createToolTip(nameEntered, '这是一个Entry.')  
createToolTip(bookChosen, '这是一个Combobox.')  
createToolTip(scr, '这是一个ScrolledText.')  
  
# 遍历monty内的所有子控件，设置它们的grid布局的内边距  
for child in monty.winfo_children():  
    child.grid_configure(padx=3, pady=1)  
# 特别设置按钮action的grid布局的内边距（这行是重复的，可以删除或修改）  
action.grid(column=2, row=1, rowspan=2, padx=6)
 
 
 # 创建一个ttk.LabelFrame控件，命名为monty2，放置在tab2上，并设置文本为'控件示范区2'  
monty2 = ttk.LabelFrame(tab2, text='控件示范区2')  
# 使用网格布局管理器放置monty2，设置列、行、内边距  
monty2.grid(column=0, row=0, padx=8, pady=4)  
  
# 创建一个整数变量chVarDis，用于与失效选项的复选框关联  
chVarDis = tk.IntVar()  
# 创建一个复选框check1，设置文本为"失效选项"，状态为禁用，并选中  
check1 = tk.Checkbutton(monty2, text="失效选项", variable=chVarDis, state='disabled')  
check1.select()    
# 使用网格布局管理器放置check1  
check1.grid(column=0, row=0, sticky=tk.W)                   
  
# 创建一个整数变量chVarUn，用于与"遵从内心"的复选框关联  
chVarUn = tk.IntVar()  
# 创建一个复选框check2，设置文本为"遵从内心"  
check2 = tk.Checkbutton(monty2, text="遵从内心", variable=chVarUn)  
# 取消选中复选框check2  
check2.deselect()     
# 使用网格布局管理器放置check2  
check2.grid(column=1, row=0, sticky=tk.W)                    
  
# 创建一个整数变量chVarEn，用于与"屈于现实"的复选框关联  
chVarEn = tk.IntVar()  
# 创建一个复选框check3，设置文本为"屈于现实"  
check3 = tk.Checkbutton(monty2, text="屈于现实", variable=chVarEn)  
# 取消选中复选框check3  
check3.deselect()  
# 使用网格布局管理器放置check3  
check3.grid(column=2, row=0, sticky=tk.W)                   
  
# 定义一个函数checkCallback，用于根据chVarUn和chVarEn的值来启用或禁用复选框  
def checkCallback(*ignoredArgs):  
    if chVarUn.get():   
        check3.configure(state='disabled')  # 如果chVarUn被选中，禁用check3  
    else:               
        check3.configure(state='normal')  # 否则，启用check3  
    if chVarEn.get():   
        check2.configure(state='disabled')  # 如果chVarEn被选中，禁用check2  
    else:               
        check2.configure(state='normal')  # 否则，启用check2  
  
# 监听chVarUn变量的变化，并在变化时调用checkCallback函数  
chVarUn.trace('w', lambda unused0, unused1, unused2 : checkCallback())      
# 监听chVarEn变量的变化，并在变化时调用checkCallback函数  
chVarEn.trace('w', lambda unused0, unused1, unused2 : checkCallback())     
  
# 定义一个列表values，包含一些字符串  
values = ["富强民主", "文明和谐", "自由平等","公正法治","爱国敬业","诚信友善"]  
  
# 定义一个函数radCall，用于根据单选按钮的选择更新monty2的文本  
def radCall():  
    radSel=radVar.get()  
    if   radSel == 0:   
        monty2.configure(text='富强民主')  
    elif radSel == 1:   
        monty2.configure(text='文明和谐')  
    elif radSel == 2:   
        monty2.configure(text='自由平等')  
    elif radSel == 3:   
        monty2.configure(text='公正法治')  
    elif radSel == 4:   
        monty2.configure(text='爱国敬业')  
    elif radSel == 5:   
        monty2.configure(text='诚信友善')  
  
# 创建一个整数变量radVar，用于与单选按钮关联  
radVar = tk.IntVar()  
# 设置radVar的初始值为99（超出values索引范围，表示初始不选中任何选项）  
radVar.set(99)      
  
# 循环创建前4个单选按钮，并放置在网格布局中的指定位置  
for col in range(4):  
    curRad = tk.Radiobutton(monty2, text=values[col], variable=radVar, value=col, command=radCall)  
    curRad.grid(column=col, row=6, sticky=tk.W, columnspan=3)  
# 循环创建后2个单选按钮，并放置在网格布局中的指定位置  
for col in range(4,6):  
    curRad = tk.Radiobutton(monty2, text=values[col], variable=radVar, value=col, command=radCall)  
    curRad.grid(column=col-4, row=7, sticky=tk.W, columnspan=3)  
  
# 创建一个样式对象style  
style = ttk.Style()  
# 配置样式"BW.TLabel"的字体  
style.configure("BW.TLabel", font=("Times", "10",'bold'))  
# 创建一个ttk.Label控件，使用配置的样式，并放置在指定位置  
ttk.Label(monty2, text="   社会主义核心价值观",style="BW.TLabel").grid(column=2, row=7,columnspan=2, sticky=tk.EW)  
  
# 创建一个ttk.LabelFrame控件，命名为labelsFrame，放置在monty2上，并设置文本为' 嵌套区域 '  
labelsFrame = ttk.LabelFrame(monty2, text=' 嵌套区域 ')  
# 使用网格布局管理器放置labelsFrame  
labelsFrame.grid(column=0, row=8,columnspan=4)  
  
# 在labelsFrame内创建两个ttk.Label控件，并设置文本  
ttk.Label(labelsFrame, text="你才25岁，你可以成为任何你想成为的人。").grid(column=0, row=0)  
ttk.Label(labelsFrame, text="不要在乎一城一池的得失，要执着。").grid(column=0, row=1,sticky=tk.W)  
  
# 遍历labelsFrame内的所有子控件，并设置它们的网格布局的内边距  
for child in labelsFrame.winfo_children():   
    child.grid_configure(padx=8,pady=4)
 
 # 创建一个名为tab3的Frame，背景色设置为#AFEEEE，并将其打包（pack）到其父容器中  
tab3 = tk.Frame(tab3, bg='#AFEEEE')  
tab3.pack()  
  
# 循环两次，创建两个画布（Canvas）  
for i in range(2):  
    # 拼接字符串以生成画布变量的名称（但此处的变量命名实际上无效，因为每次循环都会重新赋值）  
    canvas = 'canvas' + str(col)  # 注意：col变量未定义，此处应该是i或者其他有意义的变量  
    # 创建一个画布，设置宽度、高度、边框厚度和背景色，并将其网格布局（grid）到tab3中  
    canvas = tk.Canvas(tab3, width=162, height=95, highlightthickness=0, bg='#FFFF00')  
    canvas.grid(row=i, column=i)  
  
# 定义一个退出程序的函数，关闭窗口并销毁，然后退出程序  
def _quit():  
    win.quit()  
    win.destroy()  
    exit()  
  
# 创建一个菜单栏（MenuBar）并将其配置给窗口win  
menuBar = Menu(win)  
win.config(menu=menuBar)  
  
# 创建一个文件菜单（File Menu），并添加一些命令，包括新建和退出  
fileMenu = Menu(menuBar, tearoff=0)  
fileMenu.add_command(label="新建")  # 添加一个新建命令，但尚未定义其功能  
fileMenu.add_separator()  # 添加一个分隔符  
fileMenu.add_command(label="退出", command=_quit)  # 添加退出命令，绑定到_quit函数  
menuBar.add_cascade(label="文件", menu=fileMenu)  # 将文件菜单添加到菜单栏  
  
# 定义一系列显示消息框的函数  
def _msgBox1():  
    mBox.showinfo('Python Message Info Box', '通知：程序运行正常！')  # 显示信息框  
def _msgBox2():  
    mBox.showwarning('Python Message Warning Box', '警告：程序出现错误，请检查！')  # 显示警告框  
def _msgBox3():  
    mBox.showwarning('Python Message Error Box', '错误：程序出现严重错误，请退出！')  # 显示错误框  
def _msgBox4():  
    # 显示一个询问是或否的对话框，并根据用户选择显示不同的信息框  
    answer = mBox.askyesno("Python Message Dual Choice Box", "你喜欢这篇文章吗？\n您的选择是：")   
    if answer == True:  
        mBox.showinfo('显示选择结果', '您选择了“是”，谢谢参与！')  
    else:  
        mBox.showinfo('显示选择结果', '您选择了“否”，谢谢参与！')  
  
# 创建一个消息菜单（Message Menu），并添加各个消息框命令  
msgMenu = Menu(menuBar, tearoff=0)  
msgMenu.add_command(label="通知 Box", command=_msgBox1)  
msgMenu.add_command(label="警告 Box", command=_msgBox2)  
msgMenu.add_command(label="错误 Box", command=_msgBox3)  
msgMenu.add_separator()  # 添加一个分隔符  
msgMenu.add_command(label="判断对话框", command=_msgBox4)  
menuBar.add_cascade(label="消息框", menu=msgMenu)  # 将消息菜单添加到菜单栏  
  
# 设置窗口的图标  
win.iconbitmap(r'D:\_Code\SSH2Servers\mf.ico')  
  
# 将焦点设置到nameEntered控件上（但此处nameEntered未定义）  
nameEntered.focus()        
  
# 启动窗口的主循环  
win.mainloop()
