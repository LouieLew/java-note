# java-note
学习笔记

package may04;

import java.util.Scanner;

public class Telecontrol {
	/**
	 * 空调遥控器
	 * 1开 2关 3上调温度 4下调温度 5显示温度
	 * @param args
	 */
	static int temperature ;//温度
	static boolean disjunctor;
	static Scanner sc = new Scanner(System.in);
	public static void main(String[] args) {
		
		
		
		while (true){
			System.out.println("----------------------------------------");
			System.out.println("||||||||||||||--提示信息--|||||||||||||||");
			System.out.println("1,开  2,关    3,上调温度  4,下调温度    5,显示温度");
			int which = sc.nextInt();
			if(which == 1){
				on();
			}if(which == 2){
				off();
			}if(which == 3){
				temperatureArise();
			}if(which == 4){
				temperatureFall();
			}if(which == 5){
				getTemperature();
			}
		}
	}
	
	//显示温度
	private static void getTemperature() {
		// TODO Auto-generated method stub
		if(disjunctor){
			System.out.println("空调温度是：" + temperature);
		}else{
			System.out.println("空调处于关闭状态，请先打开。");
		}
	}

	//下调温度
	private static void temperatureFall() {
		// TODO Auto-generated method stub
		if(disjunctor){
			if(temperature==16){
				temperature=16;
				System.out.println("现在温度已经是最低温度，不能下调");
				return;
			}
			temperature--;
			System.out.println("现在温度是：" + temperature + "度");
		}else{
			System.out.println("空调处于关闭状态，请先打开。");
		}
	}

	//上调温度
	private static void temperatureArise() {
		// TODO Auto-generated method stub
		if(disjunctor){
			if(temperature==33){
				temperature=33;
				System.out.println("现在温度已经是最大温度，不能上调");
				return;
			}
			temperature++;
			System.out.println("现在温度是：" + temperature + "度");
		}else{
			System.out.println("空调处于关闭状态，请先打开。");
		}
	}

	//空调关闭
	private static void off() {
		// TODO Auto-generated method stub
		disjunctor = false;
		System.out.println("空调关闭");
	}

	//空调打开
	private static void on() {
		// TODO Auto-generated method stub
		disjunctor = true;
		if(temperature<16)temperature = 16;
		System.out.println("空调打开");
	}
}
