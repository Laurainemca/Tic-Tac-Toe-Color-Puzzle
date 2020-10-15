#include "stdafx.h";
#include<windows.h>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<iostream>
#include<GL\glut.h>
using namespace std;

void gstatus();
void setxy(int mousex, int mousey);
void DisplayText(std::string s, float x, float y);
void init(void);
void lineloop(void);
void mouse(int button, int state, int mousex, int mousey);
void display(void);
void Keyboardinput(unsigned char key, int x, int y);

float r, g, b, x, y;
int player = 1, f = 1, c = 10;
int stop = -1;
bool check = false;
bool plock = false;
int pstatus[3][3] = { 0,0,0,0,0,0,0,0,0 };

int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    glutInitWindowSize(600, 500);
    glutInitWindowPosition(50, 50);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
    glutCreateWindow("Tic Tac Toe Color Puzzle");
    glClearColor(1, 1, 1, 0);
    glClear(GL_COLOR_BUFFER_BIT);
    glutDisplayFunc(display);
    glutMouseFunc(mouse);
    glutKeyboardFunc(Keyboardinput);
    glutMainLoop();
}

void gstatus()
{
    if ((pstatus[0][0] == player) && (pstatus[1][1] == player) && (pstatus[2][2] == player))
        stop = player;

    if ((pstatus[0][2] == player) && (pstatus[1][1] == player) && (pstatus[2][0] == player))
        stop = player;

    for (int i = 0; i < 3; i++)
    {
        if ((pstatus[i][0] == player) && (pstatus[i][1] == player) && (pstatus[i][2] == player))
        {
            stop = player;
            break;
        }
        else if ((pstatus[0][i] == player) && (pstatus[1][i] == player) && (pstatus[2][i] == player))
        {
            stop = player;
            break;
        }
    }
    if (c == 1) stop = 0;
}

void setxy(int mousex, int mousey)
{
    if (mousex >= 150 && mousex <= 220 && mousey >= 290 && mousey <= 360 && pstatus[2][0] == 0)//1,1
    {
        x = 185; y = 185;
        c--; plock = true;
        pstatus[2][0] = player;
    }
    else if (mousex >= 220 && mousex <= 290 && mousey >= 290 && mousey <= 360 && pstatus[2][1] == 0)//1,2
    {
        x = 255; y = 185;
        c--; plock = true;
        pstatus[2][1] = player;
    }
    else if (mousex >= 290 && mousex <= 360 && mousey >= 290 && mousey <= 360 && pstatus[2][2] == 0)//1,3
    {
        x = 325; y = 185;
        c--; plock = true;
        pstatus[2][2] = player;
    }
    else if (mousex >= 150 && mousex <= 220 && mousey >= 220 && mousey <= 290 && pstatus[1][0] == 0)//2,1
    {
        x = 185; y = 255;
        c--; plock = true;
        pstatus[1][0] = player;
    }
    else if (mousex >= 220 && mousex <= 290 && mousey >= 220 && mousey <= 290 && pstatus[1][1] == 0)//2,2
    {
        x = 255; y = 255;
        c--; plock = true;
        pstatus[1][1] = player;
    }
    else if (mousex >= 290 && mousex <= 360 && mousey >= 220 && mousey <= 290 && pstatus[1][2] == 0)//2,3
    {
        x = 325; y = 255;
        c--; plock = true;
        pstatus[1][2] = player;
    }
    else if (mousex >= 150 && mousex <= 220 && mousey >= 150 && mousey <= 220 && pstatus[0][0] == 0)//3,1
    {
        x = 185; y = 325;
        c--; plock = true;
        pstatus[0][0] = player;
    }
    else if (mousex >= 220 && mousex <= 290 && mousey >= 150 && mousey <= 220 && pstatus[0][1] == 0)//3,2
    {
        x = 255; y = 325;
        c--; plock = true;
        pstatus[0][1] = player;
    }
    else if (mousex >= 290 && mousex <= 360 && mousey >= 150 && mousey <= 220 && pstatus[0][2] == 0)//3,3
    {
        x = 325; y = 325;
        c--; plock = true;
        pstatus[0][2] = player;
    }
    gstatus();
}

void DisplayText(std::string s, float x, float y)
{
    glRasterPos2f(x, y);
    for (int i = 0; i < s.size(); i++)
    {
        glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24, s[i]);
    }
}

void lineloop(void)
{
	int msgboxID = MessageBox(
        NULL,
        (LPCWSTR)L"\n 1. Two players are requred\n2.First players color is RED\n3.Second players color is GREEN ",
        (LPCWSTR)L"RULES",
         MB_ICONINFORMATION | MB_OK);
    glColor3f(1.0, 1.0, 1.0);
    glClear(GL_COLOR_BUFFER_BIT);
    glBegin(GL_LINE_LOOP); /*draw lines*/
    glVertex2f(150.0, 150.0);
    glVertex2f(150.0, 360.0);
    glVertex2f(360.0, 360.0);
    glVertex2f(360.0, 150.0);
    glEnd();
    glBegin(GL_LINE_LOOP);
    glVertex2f(220.0, 150.0);
    glVertex2f(220.0, 360.0);
    glEnd();
    glBegin(GL_LINE_LOOP);
    glVertex2f(290.0, 150.0);
    glVertex2f(290.0, 360.0);
    glEnd();
    glBegin(GL_LINE_LOOP);
    glVertex2f(150.0, 220.0);
    glVertex2f(360.0, 220.0);
    glEnd();
    glBegin(GL_LINE_LOOP);
    glVertex2f(150.0, 290.0);
    glVertex2f(360.0, 290.0);
    glEnd();
    glutSwapBuffers();
}

void mouse(int button, int state, int mousex, int mousey)
{
    if (button == GLUT_LEFT_BUTTON && state == GLUT_DOWN && c >= 0)
    {
        if (mousex >= 150 && mousex <= 360 && mousey >= 150 && mousey <= 360)
        {
            setxy(mousex, mousey);
            check = true;
            if ((player == 1) && (plock))
            {
                r = 1;
                g = 0;
                player = 2;
                plock = false;
            }
            else if ((player == 2) && (plock))
            {
                g = 1;
                r = 0;
                player = 1;
                plock = false;
            }
        }
    }
    glutPostRedisplay();
}

void display(void)
{
    glClearColor(0.0, 0.0, 0.0, 0.0);
    glColor3f(1.0, 1.0, 1.0);
    glPointSize(60);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluOrtho2D(0, 600, 0, 500);
    glColor3f(r, g, b);
    if (!check || stop >= 0)
    {
        if (stop >= 0)
        {
            glClear(GL_COLOR_BUFFER_BIT);

			//PlaySound((LPCTSTR)SND_ALIAS_SYSTEMSTART, NULL, SND_FILENAME);
			//https://docs.microsoft.com/en-us/previous-versions//dd743680(v=vs.85)?redirectedfrom=MSDN

            if (stop == 1)DisplayText("   Player-1 Wins  ", 200, 380);
            else if (stop == 2)DisplayText("   Player-2 Wins  ", 200, 380);
            else if (stop == 0)
            {
                glColor3f(1, 1, 1);
                DisplayText("  Match Draw ", 200, 380);
            }
            DisplayText("PRESS ESC TO QUIT", 200, 300);
        }
        else
        {

            lineloop();
            DisplayText("Tic Tac Toe ", 200, 380);
        }
        glFlush();
    }
    else
    {
        glBegin(GL_POINTS);
        glVertex2i(x, y);
        glEnd();
        glFlush();
    }
}

void Keyboardinput(unsigned char key, int x, int y)
{
    switch (key)
    {
    case 27:// close the screen
        exit(0);
        break;
	
    }
    glutPostRedisplay();
}
