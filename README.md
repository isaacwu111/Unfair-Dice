# Unfair-Dice

import java.util.Scanner;

public class Dice {
	
	private int diceSides = 0;
	Scanner scan = new Scanner(System.in);
	double[] chances;
	public Dice(int x)
	{
		diceSides = x;
		chances = new double[diceSides];
	}
	
	public void assignChances()
	{
		boolean equalsOne = false;
		double total = 0;
		while(equalsOne == false)
		{
			for(int i = 0; i < diceSides; i++)
			{
				System.out.println("Enter the chance of rolling a " + (i+1) + " In decimal notation");
				chances[i] = scan.nextDouble();
				total += chances[i];
			}
			if(total == 1)
			{
				equalsOne = true;
			}
			else
			{
				System.out.println("Your chances do not add to one! Reassign your values!");
			}
		}
		
	}
	double diceroll;
	public int rollDice() 
	{
		diceroll = Math.random() * diceSides+1;
		while(diceroll - (int)(diceroll) > chances[(int)(diceroll - 1)])
		{
			diceroll = Math.random() * diceSides + 1;
		}
		return (int)(diceroll);
	}

}
