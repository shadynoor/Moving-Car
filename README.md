from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL.GLUT import *
import numpy as np
from math import *

def myinit():
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluPerspective(65,1,0.1,50)
    gluLookAt(4,9,7,
              0,0,0,
              0,1,0)

    glClearColor(1,1,1,1)
    glClear(GL_COLOR_BUFFER_BIT)

def rectangle(x, y, z, x1, y1, z1, x2, y2, z2, x3, y3, z3, r, g, b, typ):
    glColor(r, g, b)
    glBegin(typ)
    glVertex3d(x, y, z)
    glVertex3d(x1, y1, z1)
    glVertex3d(x2, y2, z2)
    glVertex3d(x3, y3, z3)
    glEnd()


angle=0
forward =True
x=0

def draw():
    global angle
    global x
    global forward

    glMatrixMode(GL_MODELVIEW)
    glLoadIdentity()
    glClear(GL_COLOR_BUFFER_BIT)

    glLoadIdentity()
    rectangle(10, -5, -8,-30, -5, -8,-30, -5, 0,10, -5, 0,0.4, 0.4, 0.4,GL_POLYGON)

    glLoadIdentity()
    rectangle(10, -5, -22,-45, -5, -22,-45, -5, -8,10, -5, -8,0, 0, 0,GL_POLYGON)

    glLoadIdentity()
    rectangle(10, -5, 14,-35, -5, 14,-35, -5, 0,10, -5, 0,0, 0, 0,GL_POLYGON)

    glLoadIdentity()
    rectangle(10, -5, -22,-45, -5, -22,-45, -5, -50,10, -5, -50,0, 0, 0,GL_POLYGON)


    glColor3f(0.6, 0.3, 0)
    glScale(1,0.25,0.5)
    glTranslate(x,0,0)
    glutSolidCube(5)

    glLoadIdentity()
    glTranslate(x, 5*0.25, 0)
    glScale(0.5,0.25,0.5)
    glutSolidCube(5)

    glColor3f(0, 0, 1)
    glLoadIdentity()
    glTranslate(x+5*0.5,-5*0.25*0.5,5*0.5*0.5)
    glRotate(-angle, 0, 0, 1)
    glutSolidTorus(0.125,0.5,12,10)

    glLoadIdentity()
    glTranslate(x+5*0.5,-5*0.25*0.5,-5*0.5*0.5)
    glRotate(-angle, 0, 0, 1)
    glutSolidTorus(0.125, 0.5, 12, 10)

    glLoadIdentity()
    glTranslate(x-5*0.5,-5*0.25*0.5,-5*0.5*0.5)
    glRotate(-angle, 0, 0, 1)
    glutSolidTorus(0.125, 0.5, 12, 10)

    glLoadIdentity()
    glTranslate(x-5*0.5,-5*0.25*0.5,5*0.5*0.5)
    glRotate(-angle, 0, 0, 1)
    glutSolidTorus(0.125, 0.5, 12, 10)



    glLoadIdentity()
    glColor3f(0.6, 0.3, 0)
    glTranslate(-x+10, 0, -8)
    glScale(0.08, 0.7, 0.08)
    glutSolidCube(5)

    glLoadIdentity()
    glColor3f(0.2, 0.6, 0)
    glTranslate(-x + 10, 2.2, -8)
    glutSolidSphere(1.5,10,10)

    glLoadIdentity()
    glColor3f(0.6, 0.3, 0)
    glTranslate(-x,0,-8)
    glScale(0.08,0.7,0.08)
    glutSolidCube(5)

    glLoadIdentity()
    glColor3f(0.2, 0.6, 0)
    glTranslate(-x , 2.2, -8)
    glutSolidSphere(1.5, 10, 10)

    glLoadIdentity()
    glColor3f(0.6, 0.3, 0)
    glTranslate(-x-10, 0, -8)
    glScale(0.08, 0.7, 0.08)
    glutSolidCube(5)

    glLoadIdentity()
    glColor3f(0.2, 0.6, 0)
    glTranslate(-x-10 , 2.2, -8)
    glutSolidSphere(1.5, 10, 10)

    glLoadIdentity()
    glColor3f(0.6, 0.3, 0)
    glTranslate(-x -20, 0, -8)
    glScale(0.08, 0.7, 0.08)
    glutSolidCube(5)

    glLoadIdentity()
    glColor3f(0.2, 0.6, 0)
    glTranslate(-x - 20, 2.2, -8)
    glutSolidSphere(1.5, 10, 10)


    if forward :

       angle +=0.7
       x +=0.001
       if x> 5:
           forward=False
    else:
        angle -= 0.7
        x -= 0.001
        if x< -7:
           forward = True

    glutSwapBuffers()

glutInit()
glutInitDisplayMode(GLUT_DOUBLE |GLUT_RGB)
glutInitWindowSize(600,600)
glutCreateWindow(b"moving car")
glutDisplayFunc(draw)
glutIdleFunc(draw)
myinit()
glutMainLoop()
