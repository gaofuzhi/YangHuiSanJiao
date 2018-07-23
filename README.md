# YangHuiSanJiao

package test;
import java.util.Scanner;
/**
 * 1
 * 1 1
 * 1 2 1
 * 1 3 3 1
 * 1 4 6 4 1
 * 思想1：由易到难(下边的杨辉三角只是在左侧加了  总行数-当前行数  个空格)
 * 思想2：因为每行无法找到规律，而下一行又需要上一行的数据，所以需要存取
 * (比较合适的就是数组了 因为涉及到行与列，所以选取二维数组)
 *     1
 *    1 1
 *   1 2 1
 *  1 3 3 1
 * 1 4 6 4 1
 * @author gaofuzhi
 */
public class YangHuiSanJiao {
	public static void main(String[] args) {	
		System.out.print("please input your number to YangHuiSanJiao: ");
		Scanner input = new Scanner(System.in);
		int line = input.nextInt();
		int[][] yH = new int[line][];
		//以下这个循环主要实现数组的按需分配
		//形如：int[][] = new int[][]{{0},{0,0}...{0...0}};
		for(int i=0;i<yH.length;i++){
			yH[i] = new int[i+1];
			System.out.println(yH[i].length);
		}
		//以下这个外循环主要实现层数递增
		for(int j=0;j<yH.length;j++){
			//以下这个循环主要实现空格的输出
			for(int t = 1;t<(line-j);t++){
				System.out.print("     ");				
			}
			//以下这个循环主要实现值的改变(由0变为对应位置上的值)
			for(int k=0;k<yH[j].length;k++){
				if(k==0||k==yH[j].length-1){
					yH[j][k] = 1;
				}else{
					yH[j][k] = yH[j-1][k-1]+yH[j-1][k];
				}
			    //下面空格数==2*上面空格数-X   X越大，值越大的越整齐
				System.out.print(yH[j][k]+"       ");
			}
			System.out.print("\n"); 
		}
	}
}
