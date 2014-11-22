package project;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.Color;
import java.awt.Graphics;
import java.util.Random;

import javax.swing.JLabel;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;
import javax.swing.Timer;
public class G extends JPanel implements ActionListener, KeyListener 
{
						
Timer tm = new Timer(1000,this);
JLabel label;				

int x = 0, y = 540, velX = 0, velY = 0;
int y1 = 0,velY1 = 60,count=0;
int colorrand;
int randomPosition, randomPosition2;
int rowLength = 9;
int[] xRandom = new int[9];
int[] colorRandom1 = new int[9];
int[] color = new int[7];
public G(){
	
addKeyListener(this);
setFocusable(true);
setFocusTraversalKeysEnabled(false);
	for(int i =0 ; i< rowLength; i++){
	xRandom[i]=-1;
	}
		
		tm.start();
		
	}

public void paintComponent(Graphics g){
super.paintComponent(g);

		for(int i=0; i < rowLength; i++){
		if(xRandom[i]==-1){
		break;
		}
else{
Random rgen = new Random();
colorrand = rgen.nextInt(7);
	switch(colorRandom1[i]){
	case 0: g.setColor(Color.black);break;
	case 1: g.setColor(Color.blue);break;
	case 2: g.setColor(Color.green);break;
	case 3: g.setColor(Color.yellow);break;
	case 4: g.setColor(Color.magenta);break;
	case 5: g.setColor(Color.red);break;
	case 6: g.setColor(Color.red);break;
	case 7: g.setColor(Color.gray);break;
	}
		g.fillRect(60*xRandom[i], i*velY1, 60,60);

}
					g.setColor(Color.RED);
					g.fillRect(x, y, 30,30);
					repaint();
		}
}
public void actionPerformed(ActionEvent e){
		
		Random rgen = new Random();  
		randomPosition = rgen.nextInt(5);

		for(int i=rowLength-1;i>0;i--){
				xRandom[i]= xRandom[i-1];
				colorRandom1[i] = colorRandom1[i-1];
		}
		colorRandom1[0] = rgen.nextInt(7);
		xRandom[0] = randomPosition;
		repaint();
					
					
					if(x>=((xRandom[8]*60)-25)&&x<=(xRandom[8]*60)-85){
							count++;
							label = new JLabel("hello");
							add(label);
							
					}
					
	
}
public void keyPressed(KeyEvent e)
{
int c = e.getKeyCode();

		if(c == KeyEvent.VK_LEFT)
		{
			x=x-7;
		}
		if(c == KeyEvent.VK_RIGHT){
			x=x+7;
		}
}

		public static void main(String[] args)
		{
		G t=new G();
		JFrame jf = new JFrame();
		jf.setTitle("Square Tiles");
		jf.setSize(320,610);
		jf.setResizable(true);
		jf.setVisible(true);
		jf.setLocationRelativeTo(null);
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		jf.add(t);
		
		}

	}	
