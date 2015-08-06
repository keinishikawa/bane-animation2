//61316444 西川　慶
//マス・バネ・ダンパのアニメーションとcsvファイルへの保存

#include <windows.h>
#include <math.h>
#include <iostream>
#include <stdexcept>
#include <fstream>
#include <string>
#include <string.h>
#include "sdglib.h"
using namespace std;

//変数の定義

static double xx, yy, tt, rr, vv, xx1, yy1, tt1, rr1, vv1;
static double graph[1000], graph1[1000];
char buff1[100];
char string_s[] = "x";
char string_s1[] = "t";

//アウトプットファイルを開く
ofstream outfile;


//ディスプレイに関する動作

void displayfunc(){
	using namespace SDGLibF;
	int i;
	char buff[100];

	// Set drawing plane
	Before();

	//座標の作成
	SetColor(0.0, 0.0, 0.0);
	DrawLine(1.0, 0.0, 0.0, 600.0, 0.0);

	//動く円の作成（上から赤、青）
	SetColor(1.0, 0.0, 0.0);
	DrawCircle(3.0, tt, xx, rr);
	for (i = 0; i < tt - 1; i++)DrawLine(3.0, i, graph[i], i + 1, graph[i + 1]);
	SetColor(0.0, 0.0, 1.0);
	DrawCircle(1.0, tt1, xx1, rr1);
	for (i = 0; i < tt1 - 1; i++)DrawLine(1.0, i, graph1[i], i + 1, graph1[i + 1]);

	//画面左上にデータの表示
	SetColor(1.0, 0.0, 0.0);
	sprintf_s(buff, "tt=%7.2f xx=%7.2f rr=%7.2f ", tt, xx, rr);
	DrawString(30, 270, buff);
	SetColor(0.0, 0.0, 1.0);
	sprintf_s(buff, "tt1=%7.2f xx1=%7.2f rr1=%7.2f ", tt1, xx1, rr1);
	DrawString(30, 250, buff);

	//SAVEDATA!の表示
	SetColor(1.0, 0.0, 0.0);
	DrawString(30, 200, buff1);

	//x,ｔの表示
	SetColor(0.0, 0.0, 0.0);
	DrawString(20, 230, string_s);
	DrawString(570, 20, string_s1);

	//土台の描画
	SetColor(0.0, 0.0, 0.0);
	DrawLine(2.0, 20.0, -250.0, 580.0, -250.0);
	DrawLine(2.0, 580.0, -250.0, 580.0, -260.0);
	DrawLine(2.0, 10.0, -260.0, 580.0, -260.0);
	DrawLine(2.0, 10.0, -260.0, 10.0, -130.0);
	DrawLine(2.0, 10.0, -130.0, 20.0, -130.0);
	DrawLine(2.0, 20.0, -250.0, 20.0, -130.0);

	//赤い方のアニメーション
	SetColor(1.0, 0.0, 0.0);
	DrawLine(2.0, 20.0, -200.0, 60.0, -200.0);
	DrawLine(2.0, 60.0, -200.0, 70.0 + xx / 5, -170);
	DrawLine(2.0, 70.0 + xx / 5, -170, 80.0 + 2 * xx / 5, -230.0);
	DrawLine(2.0, 80.0 + 2 * xx / 5, -230, 90.0 + 3 * xx / 5, -170.0);
	DrawLine(2.0, 90.0 + 3 * xx / 5, -170, 100.0 + 4 * xx / 5, -230.0);
	DrawLine(2.0, 100.0 + 4 * xx / 5, -230, 110.0 + 5 * xx / 5, -170.0);
	DrawLine(2.0, 110.0 + 5 * xx / 5, -170, 120.0 + 6 * xx / 5, -230.0);
	DrawLine(2.0, 120.0 + 6 * xx / 5, -230, 130.0 + 7 * xx / 5, -170.0);
	DrawLine(2.0, 130.0 + 7 * xx / 5, -170, 140.0 + 8 * xx / 5, -230.0);
	DrawLine(2.0, 140.0 + 8 * xx / 5, -230, 150.0 + 9 * xx / 5, -170.0);
	DrawLine(2.0, 150.0 + 9 * xx / 5, -170, 160.0 + 10 * xx / 5, -230.0);
	DrawLine(2.0, 160.0 + 10 * xx / 5, -230, 170.0 + 11 * xx / 5, -200.0);
	DrawLine(2.0, 170.0 + 11 * xx / 5, -200.0, 210.0 + 11 * xx / 5, -200.0);
	DrawLine(2.0, 210.0 + 11 * xx / 5, -250.0, 210.0 + 11 * xx / 5, -150.0);
	DrawLine(2.0, 210.0 + 11 * xx / 5, -150.0, 260.0 + 11 * xx / 5, -150.0);
	DrawLine(2.0, 260.0 + 11 * xx / 5, -150.0, 260.0 + 11 * xx / 5, -250.0);
	DrawLine(2.0, 210.0 + 11 * xx / 5, -250.0, 260.0 + 11 * xx / 5, -250.0);

	//青い方のアニメーション
	SetColor(0.0, 0.0, 1.0);
	DrawLine(2.0, 20.0, -200.0, 60.0, -200.0);
	DrawLine(2.0, 60.0, -200.0, 70.0 + xx1 / 5, -170);
	DrawLine(2.0, 70.0 + xx1 / 5, -170, 80.0 + 2 * xx1 / 5, -230.0);
	DrawLine(2.0, 80.0 + 2 * xx1 / 5, -230, 90.0 + 3 * xx1 / 5, -170.0);
	DrawLine(2.0, 90.0 + 3 * xx1 / 5, -170, 100.0 + 4 * xx1 / 5, -230.0);
	DrawLine(2.0, 100.0 + 4 * xx1 / 5, -230, 110.0 + 5 * xx1 / 5, -170.0);
	DrawLine(2.0, 110.0 + 5 * xx1 / 5, -170, 120.0 + 6 * xx1 / 5, -230.0);
	DrawLine(2.0, 120.0 + 6 * xx1 / 5, -230, 130.0 + 7 * xx1 / 5, -170.0);
	DrawLine(2.0, 130.0 + 7 * xx1 / 5, -170, 140.0 + 8 * xx1 / 5, -230.0);
	DrawLine(2.0, 140.0 + 8 * xx1 / 5, -230, 150.0 + 9 * xx1 / 5, -170.0);
	DrawLine(2.0, 150.0 + 9 * xx1 / 5, -170, 160.0 + 10 * xx1 / 5, -230.0);
	DrawLine(2.0, 160.0 + 10 * xx1 / 5, -230, 170.0 + 11 * xx1 / 5, -200.0);
	DrawLine(2.0, 170.0 + 11 * xx1 / 5, -200.0, 210.0 + 11 * xx1 / 5, -200.0);
	DrawLine(2.0, 210.0 + 11 * xx1 / 5, -250.0, 210.0 + 11 * xx1 / 5, -150.0);
	DrawLine(2.0, 210.0 + 11 * xx1 / 5, -150.0, 260.0 + 11 * xx1 / 5, -150.0);
	DrawLine(2.0, 260.0 + 11 * xx1 / 5, -150.0, 260.0 + 11 * xx1 / 5, -250.0);
	DrawLine(2.0, 210.0 + 11 * xx1 / 5, -250.0, 260.0 + 11 * xx1 / 5, -250.0);

	After(); // Set drawn plane

}




//暇なときに行なう動作

void simulation(void){
	using namespace SDGLibF;

	//物理的データの入力
	static int count = 0, n;
	static double x = 0.0, vx = 1.0, ax = 0.0;
	static double m = 1.0, D = 1.0, k = 100.0, f = 1.0;
	static double x1 = 0.0, vx1 = 1.0, ax1 = 0.0;
	static double m1 = 1.0, D1 = 1.0, k1 = 10.0, f1 = 10.0;
	static double dt = 0.002, g = 9.8, mag = 700.0;

	//赤い方の運動の式
	n = (int)(1.0 / dt);
	if (vv > 0.0) { vx += 0.0; vv = 0.0; }
	ax = (f - D*vx - k*x) / m;
	x = x + vx*dt;
	vx = vx + ax*dt;
	tt += 0.1; xx = x*mag;
	if (tt >= 600.0) tt = 0.0;
	if (x < 0.0) { vx = fabs(vx)*0.9; yy = 0.0; }
	graph[(int)tt] = xx;

	//青い方の運動の式
	n = (int)(1.0 / dt);
	if (vv1 > 0.0) { vx1 += 0.0; vv1 = 0.0; }
	ax1 = (f - D1*vx1 - k1*x1) / m1;
	x1 = x1 + vx1*dt;
	vx1 = vx1 + ax1*dt;
	tt1 += 0.1; xx1 = x1*mag;
	if (tt1 >= 600.0) tt1 = 0.0;
	if (x1 < 0.0) { vx1 = fabs(vx1)*0.9; yy1 = 0.0; }
	graph1[(int)tt1] = xx1;

	//ディスプレイ更新
	if (((count++) % (1)) == 0)  ReDraw();
}




//キーボードに関する動作

void keyboardfunc(unsigned char k, int x, int y){
	using namespace SDGLibF;
	switch (k) {
	case 27:  exit(0);
	case 'C': SetCursor(GLUT_CURSOR_RIGHT_ARROW); break;
	case 'c': SetCursor(GLUT_CURSOR_WAIT); break;
		//球の大きさ変更
	case 'r': rr += 5.0; break;
	case 'R': rr -= 5.0; break;
	case 'v':
	case 'V': vv = 1.0; break;
	case 's': IdleFunc(simulation); break;
		//SAVEDATA!とディスプレイに表示し、そのデータをcsvファイルに保存する動作
	case 'S': sprintf_s(buff1, "SAVE DATA!"); ReDraw(); IdleFunc(NULL);
		outfile.open("simudata.csv");
		outfile << "xx" << "," << "tt" << endl;
		outfile << xx << "," << tt << endl;
		outfile.close();
		break;
	default:break;
	}
}




//メイン関数

int main(void){
	//画面表示の設定
	SDGLib mygraphic(600, 600, "- 2D Graphics - (61316444 Kei Nishikawa)", 0.0, 600.0, -300.0, 300.0);
	mygraphic.SetCursor(GLUT_CURSOR_WAIT);
	mygraphic.Display(displayfunc);
	mygraphic.Keyboard(keyboardfunc);
	//初期値の設定
	tt = 0.0; xx = 0.0; yy = 0.0; rr = 10.0; tt1 = 0.0; xx1 = 0.0; yy1 = 0.0; rr1 = 10.0;
	mygraphic.Start();
	return 0;
}


/*
考察・説明
・質量，減衰係数，バネ定数を変えて２種類の減衰比を定め，それぞれの場合について，マス位置の時間変化を図示し、
　そのマス・バネ・ダンパの動きをアニメーションで描画するプログラムである。
 ・アニメーションの描画では、線分の終点を次の線分の始点と同じ座標に設定することでバネの連続性を表現した。
 ・csvファイルにデータを保存するときは、","で区切ると隣のセルにデータ保存場所が移動する。
 */


