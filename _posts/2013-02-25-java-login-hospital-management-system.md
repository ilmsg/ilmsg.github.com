---
layout: post
title: "ส่วน login ระบบสารสนเทศบริหารจัดการโรงพยาบาล"
description: "ส่วน login เข้าระบบ ของ ระบบสารสนเทศบริหารจัดการโรงพยาบาล"
category: snippet code
tags: [java, desktop application]
---
{% include JB/setup %}

ระบบสารสนเทศบริหารจัดการโรงพยาบาล

ซอร์ดโค้ดตัวเต็ม Main.java

	package com.ilmsg.hms;
	
	import java.awt.*;
	import java.awt.event.*;
	import javax.swing.*;
	
	public class Main extends JFrame implements ActionListener {
		
		public Main(){
			new Login();
		}
		
		public static void main(String[] args) {
			new Main();
		}
		
		@Override
		public void actionPerformed(ActionEvent arg0) {
					
		}
	}

ซอร์ดโค้ดตัวเต็ม Login.java

	package com.ilmsg.hms;
	
	import java.awt.*;
	import java.awt.event.*;
	
	import javax.swing.*;
	import java.io.FileInputStream;
	import java.io.IOException;
	import java.util.Properties;
	
	public class Login extends JFrame implements ActionListener {
		
		private JDialog frame;
		private JPanel panelNorth, panelCenter, panelSouth;
		private JButton buttonLogin, buttonExit;
		private JLabel labelHeader, labelUsername, labelPassword;
		private JTextField textFieldUserName;
		private JPasswordField textFieldPassword;
	
		private String strUsername = "";		
		private Properties prop;
		
		public Login(){
			
			Dimension screen = Toolkit.getDefaultToolkit().getScreenSize();		
			prop = new Properties();
			 
			try {
				//prop.load( Login.class.getClassLoader().getResourceAsStream("config.properties") );
				prop.load(new FileInputStream("config.properties"));  
			} catch (IOException ex) {
				ex.printStackTrace();
			}
			
			labelHeader = new JLabel(prop.getProperty("labelHeader"));
			labelHeader.setFont(new Font("tahoma", Font.BOLD, 24));
	
			labelUsername = new JLabel(prop.getProperty("labelUsername") + ":");
			labelUsername.setFont(new Font("tahoma", Font.BOLD, 14));
			labelUsername.setHorizontalAlignment(SwingConstants.RIGHT);
			labelUsername.setPreferredSize(new Dimension(70,20));  
			
			labelPassword = new JLabel(prop.getProperty("labelPassword") + ":");
			labelPassword.setFont(new Font("tahoma", Font.BOLD, 14));
			labelPassword.setHorizontalAlignment(SwingConstants.RIGHT);
			labelPassword.setPreferredSize(new Dimension(70, 20));  
			
			textFieldUserName = new JTextField(20);	
			textFieldUserName.setPreferredSize(new Dimension(20,20)); 
			
			textFieldPassword = new JPasswordField(20);
			textFieldPassword.setPreferredSize(new Dimension(20,20)); 				
			   
			buttonLogin = new JButton(prop.getProperty("buttonLogin"), new ImageIcon("images/lock32.png"));
			buttonLogin.setFont(new Font("tahoma", Font.BOLD, 14));
			buttonLogin.addActionListener(this);
			
			buttonExit = new JButton(prop.getProperty("buttonExit"), new ImageIcon("images/exit32.png"));
			buttonExit.setFont(new Font("tahoma", Font.BOLD, 14));
			buttonExit.addActionListener(this);
			
			panelNorth = new JPanel();
			panelNorth.setLayout(new FlowLayout());
			panelNorth.add(labelHeader);
			panelNorth.setOpaque(true);
			
			JPanel panelUsername = new JPanel();
			panelUsername.setLayout(new FlowLayout());
			panelUsername.add(labelUsername);
			panelUsername.add(textFieldUserName);
			
			JPanel panelPassword = new JPanel();
			panelPassword.setLayout(new FlowLayout());
			panelPassword.add(labelPassword);
			panelPassword.add(textFieldPassword);
			
			panelCenter = new JPanel();
			panelCenter.setLayout(new FlowLayout());
			panelCenter.setLayout(new FlowLayout());
			panelCenter.add( panelUsername );
			panelCenter.add( panelPassword );
			
			panelSouth = new JPanel();
			panelSouth.setLayout(new FlowLayout());
			panelSouth.add(buttonLogin);
			panelSouth.add(buttonExit);
			panelSouth.setOpaque(true);
			frame = new JDialog(new JFrame(), prop.getProperty("labelHeader"));
			frame.setSize(500,200);
			frame.setResizable(false);
			frame.setAlwaysOnTop(true);
			
			Container pane = frame.getContentPane();   
			pane.setLayout(new BorderLayout());
			pane.add(panelNorth, BorderLayout.NORTH);
			pane.add(panelCenter, BorderLayout.CENTER);
			pane.add(panelSouth, BorderLayout.SOUTH);
			frame.setLocation((screen.width - 500)/2,((screen.height-350)/2));	
			frame.setVisible(true);
			frame.addWindowListener(new WindowAdapter(){
				public void windowClosing(WindowEvent e){
					System.exit(0);
				}
			});
		}
	
		@Override
		public void actionPerformed(ActionEvent e) {
			if( e.getSource() == buttonLogin ){
				JOptionPane.showMessageDialog((Component)null, "Welcome.", prop.getProperty("labelWelcome"), JOptionPane.INFORMATION_MESSAGE);
			}
		}
	}

ไพล์ config.properties

	labelHeader=\u0E23\u0E30\u0E1A\u0E1A\u0E2A\u0E32\u0E23\u0E2A\u0E19\u0E40\u0E17\u0E28\u0E1A\u0E23\u0E34\u0E2B\u0E32\u0E23\u0E08\u0E31\u0E14\u0E01\u0E32\u0E23\u0E42\u0E23\u0E07\u0E1E\u0E22\u0E32\u0E1A\u0E32\u0E25
	labelUsername=\u0E0A\u0E37\u0E48\u0E2D\u0E1C\u0E39\u0E49\u0E43\u0E0A\u0E49
	labelPassword=\u0E23\u0E2B\u0E31\u0E2A\u0E1C\u0E48\u0E32\u0E19
	labelWelcome=\u0E22\u0E34\u0E19\u0E14\u0E35\u0E15\u0E49\u0E2D\u0E19\u0E23\u0E31\u0E1A
	buttonLogin=\u0E40\u0E02\u0E49\u0E32\u0E23\u0E30\u0E1A\u0E1A
	buttonExit=\u0E2D\u0E2D\u0E01\u0E23\u0E30\u0E1A\u0E1A


![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-25_004320.png)