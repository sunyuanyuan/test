# test1
public class Hello{
   public static void main(String[] args){
	System.out.println("Hello World!");
   }
}
#test2import java.util.Scanner;
import java.io.*;

public class T{
    public static void main(String[] args){
	int[]a = null;
	Scanner input = new Scanner(System.in);
	int len=0;
	System.out.print("请输入数组的长度：");
	try{
	    len = Integer.parseInt(input.nextLine());
	}catch(Exception e){
	
	}
	
	a = new int[len];
	System.out.println("a.length ="+a.length);
	
	for(int i=0;i<a.length;i++){
	    System.out.print("请输入数值：");
	    a[i] = input.nextInt();
	}
	
	System.out.println();
	System.out.print("该数组为：");
	for(int i=0;i<a.length;i++){
	    
	    System.out.print(a[i] + " ");
	}
	
	
	int sum = 0,max = 0;
	for(int i=0;i<a.length;i++){
	    sum = 0;
	    for(int j=i;j<a.length;++j){
		sum += a[j];
		if(sum>max)
		    max = sum;
	    }
	}
	
	System.out.println();
	System.out.println("该数组之和的最大值为 "+max);

    }
    
    
}
import java.util.Scanner;
import java.io.*;

public class T{
    public static void main(String[] args){
	int[]a = null;
	Scanner input = new Scanner(System.in);
	int len=0;
	System.out.print("请输入数组的长度：");
	try{
	    len = Integer.parseInt(input.nextLine());
	}catch(Exception e){
	
	}
	
	a = new int[len];
	System.out.println("a.length ="+a.length);
	
	for(int i=0;i<a.length;i++){
	    System.out.print("请输入数值：");
	    a[i] = input.nextInt();
	}
	
	System.out.println();
	System.out.print("该数组为：");
	for(int i=0;i<a.length;i++){
	    
	    System.out.print(a[i] + " ");
	}
	
	
	int sum = 0,max = 0;
	for(int i=0;i<a.length;i++){
	    sum = 0;
	    for(int j=i;j<a.length;++j){
		sum += a[j];
		if(sum>max)
		    max = sum;
	    }
	}
	
	System.out.println();
	System.out.println("该数组之和的最大值为 "+max);

    }
    
    
}
#test3
import java.util.Scanner;

public class Y{
    public static void main(String[] args) {
	Scanner input = new Scanner(System.in);
	System.out.print("请输入英文：");
	String str = input.nextLine();
        String[] strArr = str.split("\\s+|[,]");
        StringBuffer result = new StringBuffer();
        for(int i = strArr.length -1;i >=0; i--){
            result.append(strArr[i] + " ");
        }
        result.setCharAt(str.length()-3, ' ');
        System.out.println("颠倒顺序后的结果为："+result.toString());
}}
#test4
/// <summary>
    /// 使窗口的中的指定控件支持运行时移动
    /// TODO:运行时缩放
    /// </summary>
    public class ControlMoveResize
    {
        #region 私有成员
        bool IsMoving = false;
        Point pCtrlLastCoordinate = new Point(0,0);
        Point pCursorOffset = new Point(0, 0);
        Point pCursorLastCoordinate = new Point(0, 0);
        private Control ctrl = null;
        private ScrollableControl Containe = null;
        #endregion
        #region 私有方法
        /// <summary>
        /// 在鼠标左键按下的状态记录鼠标当前的位置,以及被移动组件的当前位置
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void MouseDown(object sender, MouseEventArgs e)
        {
            if (Containe == null)
            {
                return;
            }
            if (e.Button == MouseButtons.Left)
            {
                IsMoving = true;
                pCtrlLastCoordinate.X = ctrl.Left;
                pCtrlLastCoordinate.Y = ctrl.Top;
                pCursorLastCoordinate.X = Cursor.Position.X;
                pCursorLastCoordinate.Y = Cursor.Position.Y;
            }
        }
        private void MouseMove(object sender, MouseEventArgs e)
        {
            if (Containe == null)
            {
                return;
            }
                
            if (e.Button == MouseButtons.Left)
            {
                if (this.IsMoving)
                {
                    Point pCursor = new Point(Cursor.Position.X, Cursor.Position.Y);
                  
                    pCursorOffset.X = pCursor.X - pCursorLastCoordinate.X;
               
                    pCursorOffset.Y = pCursor.Y - pCursorLastCoordinate.Y;
                    ctrl.Left = pCtrlLastCoordinate.X + pCursorOffset.X;
                    ctrl.Top = pCtrlLastCoordinate.Y + pCursorOffset.Y;
                }

            }
        }
 
        private void MouseUp(object sender, MouseEventArgs e)
        {
            if (Containe == null)
            {
                return;
            }
            if (this.IsMoving)
            {
                if (pCursorOffset.X == 0 && pCursorOffset.Y == 0)
                {
                    return;
                }
                if ((pCtrlLastCoordinate.X + pCursorOffset.X + ctrl.Width) > 0)
                {
                    ctrl.Left = pCtrlLastCoordinate.X + pCursorOffset.X;
                }
                else
                {
                    ctrl.Left = 0;
                }
                if ((pCtrlLastCoordinate.Y + pCursorOffset.Y + ctrl.Height) > 0)
                {
                    ctrl.Top = pCtrlLastCoordinate.Y + pCursorOffset.Y;
                }
                else
                {
                    ctrl.Top = 0;
                }
                pCursorOffset.X = 0;
                pCursorOffset.Y = 0;
            }
        }
        #endregion
        #region 构造函数
        /// <summary>
        /// 获取被移动控件对象和容器对象
        /// </summary>
        /// <param name="c">被设置为可运行时移动的控件</param>
        /// <param name="parentContain">可移动控件的容器</param>
        public ControlMoveResize(Control c, ScrollableControl parentContain)
        {
            ctrl = c;
            this.Containe = parentContain;
            ctrl.MouseDown += new MouseEventHandler(MouseDown);
            ctrl.MouseMove += new MouseEventHandler(MouseMove);
            ctrl.MouseUp += new MouseEventHandler(MouseUp);
        }
        #endregion
