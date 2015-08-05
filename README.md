# bane-animation2
バネのアニメーション

//61316444 êºêÏÅ@åc
//É}ÉXÅEÉoÉlÅEÉ_ÉìÉpÇÃÉAÉjÉÅÅ[ÉVÉáÉìÇ∆csvÉtÉ@ÉCÉãÇ÷ÇÃï€ë∂

#include <windows.h>
#include <math.h>
#include <iostream>
#include <stdexcept>
#include <fstream>
#include <string>
#include <string.h>
#include "sdglib.h"
using namespace std;

//ïœêîÇÃíËã`

static double xx, yy, tt, rr, vv, xx1, yy1, tt1, rr1, vv1;
static double graph[1000], graph1[1000];
char buff1[100];
char string_s[] = "x";
char string_s1[] = "t";

//ÉAÉEÉgÉvÉbÉgÉtÉ@ÉCÉãÇäJÇ≠
ofstream outfile;


//ÉfÉBÉXÉvÉåÉCÇ…ä÷Ç∑ÇÈìÆçÏ

void displayfunc(){
	using namespace SDGLibF;
	int i;
	char buff[100];

	// Set drawing plane
	Before();

	//ç¿ïWÇÃçÏê¨
	SetColor(0.0, 0.0, 0.0);
	DrawLine(1.0, 0.0, 0.0, 600.0, 0.0);

	//ìÆÇ≠â~ÇÃçÏê¨Åiè„Ç©ÇÁê‘ÅAê¬Åj
	SetColor(1.0, 0.0, 0.0);
	DrawCircle(3.0, tt, xx, rr);
	for (i = 0; i < tt - 1; i++)DrawLine(3.0, i, graph[i], i + 1, graph[i + 1]);
	SetColor(0.0, 0.0, 1.0);
	DrawCircle(1.0, tt1, xx1, rr1);
	for (i = 0; i < tt1 - 1; i++)DrawLine(1.0, i, graph1[i], i + 1, graph1[i + 1]);

	//âÊñ ç∂è„Ç…ÉfÅ[É^ÇÃï\é¶
	SetColor(1.0, 0.0, 0.0);
	sprintf_s(buff, "tt=%7.2f xx=%7.2f rr=%7.2f ", tt, xx, rr);
	DrawString(30, 270, buff);
	SetColor(0.0, 0.0, 1.0);
	sprintf_s(buff, "tt1=%7.2f xx1=%7.2f rr1=%7.2f ", tt1, xx1, rr1);
	DrawString(30, 250, buff);

	//SAVEDATA!ÇÃï\é¶
	SetColor(1.0, 0.0, 0.0);
	DrawString(30, 200, buff1);

	//x,ÇîÇÃï\é¶
	SetColor(0.0, 0.0, 0.0);
	DrawString(20, 230, string_s);
	DrawString(570, 20, string_s1);

	//ìyë‰ÇÃï`âÊ
	SetColor(0.0, 0.0, 0.0);
	DrawLine(2.0, 20.0, -250.0, 580.0, -250.0);
	DrawLine(2.0, 580.0, -250.0, 580.0, -260.0);
	DrawLine(2.0, 10.0, -260.0, 580.0, -260.0);
	DrawLine(2.0, 10.0, -260.0, 10.0, -130.0);
	DrawLine(2.0, 10.0, -130.0, 20.0, -130.0);
	DrawLine(2.0, 20.0, -250.0, 20.0, -130.0);

	//ê‘Ç¢ï˚ÇÃÉAÉjÉÅÅ[ÉVÉáÉì
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

	//ê¬Ç¢ï˚ÇÃÉAÉjÉÅÅ[ÉVÉáÉì
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




//â…Ç»Ç∆Ç´Ç…çsÇ»Ç§ìÆçÏ

void simulation(void){
	using namespace SDGLibF;

	//ï®óùìIÉfÅ[É^ÇÃì¸óÕ
	static int count = 0, n;
	static double x = 0.0, vx = 1.0, ax = 0.0;
	static double m = 1.0, D = 1.0, k = 100.0, f = 1.0;
	static double x1 = 0.0, vx1 = 1.0, ax1 = 0.0;
	static double m1 = 1.0, D1 = 1.0, k1 = 10.0, f1 = 10.0;
	static double dt = 0.002, g = 9.8, mag = 700.0;

	//ê‘Ç¢ï˚ÇÃâ^ìÆÇÃéÆ
	n = (int)(1.0 / dt);
	if (vv > 0.0) { vx += 0.0; vv = 0.0; }
	ax = (f - D*vx - k*x) / m;
	x = x + vx*dt;
	vx = vx + ax*dt;
	tt += 0.1; xx = x*mag;
	if (tt >= 600.0) tt = 0.0;
	if (x < 0.0) { vx = fabs(vx)*0.9; yy = 0.0; }
	graph[(int)tt] = xx;

	//ê¬Ç¢ï˚ÇÃâ^ìÆÇÃéÆ
	n = (int)(1.0 / dt);
	if (vv1 > 0.0) { vx1 += 0.0; vv1 = 0.0; }
	ax1 = (f - D1*vx1 - k1*x1) / m1;
	x1 = x1 + vx1*dt;
	vx1 = vx1 + ax1*dt;
	tt1 += 0.1; xx1 = x1*mag;
	if (tt1 >= 600.0) tt1 = 0.0;
	if (x1 < 0.0) { vx1 = fabs(vx1)*0.9; yy1 = 0.0; }
	graph1[(int)tt1] = xx1;

	//ÉfÉBÉXÉvÉåÉCçXêV
	if (((count++) % (1)) == 0)  ReDraw();
}




//ÉLÅ[É{Å[ÉhÇ…ä÷Ç∑ÇÈìÆçÏ

void keyboardfunc(unsigned char k, int x, int y){
	using namespace SDGLibF;
	switch (k) {
	case 27:  exit(0);
	case 'C': SetCursor(GLUT_CURSOR_RIGHT_ARROW); break;
	case 'c': SetCursor(GLUT_CURSOR_WAIT); break;
		//ãÖÇÃëÂÇ´Ç≥ïœçX
	case 'r': rr += 5.0; break;
	case 'R': rr -= 5.0; break;
	case 'v':
	case 'V': vv = 1.0; break;
	case 's': IdleFunc(simulation); break;
		//SAVEDATA!Ç∆ÉfÉBÉXÉvÉåÉCÇ…ï\é¶ÇµÅAÇªÇÃÉfÅ[É^ÇcsvÉtÉ@ÉCÉãÇ…ï€ë∂Ç∑ÇÈìÆçÏ
	case 'S': sprintf_s(buff1, "SAVE DATA!"); ReDraw(); IdleFunc(NULL);
		outfile.open("simudata.csv");
		outfile << "xx" << "," << "tt" << endl;
		outfile << xx << "," << tt << endl;
		outfile.close();
		break;
	default:break;
	}
}




//ÉÅÉCÉìä÷êî

int main(void){
	//âÊñ ï\é¶ÇÃê›íË
	SDGLib mygraphic(600, 600, "- 2D Graphics - (61316444 Kei Nishikawa)", 0.0, 600.0, -300.0, 300.0);
	mygraphic.SetCursor(GLUT_CURSOR_WAIT);
	mygraphic.Display(displayfunc);
	mygraphic.Keyboard(keyboardfunc);
	//èâä˙ílÇÃê›íË
	tt = 0.0; xx = 0.0; yy = 0.0; rr = 10.0; tt1 = 0.0; xx1 = 0.0; yy1 = 0.0; rr1 = 10.0;
	mygraphic.Start();
	return 0;
}


/*
çlé@ÅEê‡ñæ
ÅEéøó ÅCå∏êäåWêîÅCÉoÉlíËêîÇïœÇ¶ÇƒÇQéÌóﬁÇÃå∏êäî‰ÇíËÇﬂÅCÇªÇÍÇºÇÍÇÃèÍçáÇ…Ç¬Ç¢ÇƒÅCÉ}ÉXà íuÇÃéûä‘ïœâªÇê}é¶ÇµÅA
Å@ÇªÇÃÉ}ÉXÅEÉoÉlÅEÉ_ÉìÉpÇÃìÆÇ´ÇÉAÉjÉÅÅ[ÉVÉáÉìÇ≈ï`âÊÇ∑ÇÈÉvÉçÉOÉâÉÄÇ≈Ç†ÇÈÅB
 ÅEÉAÉjÉÅÅ[ÉVÉáÉìÇÃï`âÊÇ≈ÇÕÅAê¸ï™ÇÃèIì_ÇéüÇÃê¸ï™ÇÃénì_Ç∆ìØÇ∂ç¿ïWÇ…ê›íËÇ∑ÇÈÇ±Ç∆Ç≈ÉoÉlÇÃòAë±ê´Çï\åªÇµÇΩÅB
 ÅEcsvÉtÉ@ÉCÉãÇ…ÉfÅ[É^Çï€ë∂Ç∑ÇÈÇ∆Ç´ÇÕÅA","Ç≈ãÊêÿÇÈÇ∆ó◊ÇÃÉZÉãÇ…ÉfÅ[É^ï€ë∂èÍèäÇ™à⁄ìÆÇ∑ÇÈÅB
 */


