package artpricingsystem;

import java.io.File;
import java.io.IOException;
import java.io.RandomAccessFile;
import java.util.Date;
import java.util.Scanner;

public class SoldPainting extends BoughtPainting
{
    private Date dateOfSale;
    private String nameOfBuyer;
    private String addressOfBuyer;
    private double actualSellingPrice; 
    
    //Desc: constructor for SoldPainting
    //Post: allows class to set the value of the dateOfSale, nameOfBuyer,
    //		addressOfBuyer, and actualSellingPrice field in a record
    SoldPainting(String fname, String lname, String work, Date dwork, 
    String clas, double h, double w, String med, String sub, double max, 
    Date dop, String nos, String aos, double p, double t, Date dos, String nob, 
    String aob, double actualsell)
    {
        artistFirstName=fname;
        artistLastName=lname;
        titleOfWork=work;
        dateOfWork=dwork;
        classification=clas;
        height=h;
        width=w;
        medium=med;
        subject=sub;
        suggestedMaximumPurchasePrice=max;
        dateOfPurchase=dop;
        nameOfSeller=nos;
        addressOfSeller=aos;
        actualPurchasePrice=p;
        targetSellingPrice=t;
        dateOfSale=dos;
        nameOfBuyer=nob;
        addressOfBuyer=aob;
        actualSellingPrice=actualsell;
    }

    SoldPainting()
    {    
    }
    //Desc: allows class to access the dateOfSale field in a record
    //Return: dateOfSale
    public Date getDateOfSale() 
    {
	return dateOfSale;
    }
	
    //Desc: allows class to set the value of the dateOfSale field in a record
    //Post: dateOfSale is set to d
    public void setDateOfSale(Date d)
    {
        dateOfSale=d;
    }
	
    //Desc:allows class to access the nameOfBuyer field in a record
    //Return: nameOfBuyer
    public String getNameOfBuyer()
    {
        return nameOfBuyer;
    }
	
    //Desc: allows class to set the value of the nameOfBuyer field in a record
    //Post: nameOfBuyer is set to n
    public void setNameOfBuyer(String n)
    {
        nameOfBuyer=n;
    }
	
    //Desc:allows class to access the addressOfBuyer field in a record
    //Return: addressOfBuyer
    public String getAddressOfBuyer() 
    {
        return addressOfBuyer;
    }

    //Desc: allows class to set the value of the addressOfBuyer field in record
    //Post: addressOfBuyer is set to a
    public void setAddressOfBuyer(String a)
    {
        addressOfBuyer=a;
    }
	
    //Desc:allows class to access the actualSellingPrice field in a record
    //Return: actualSellingPrice
    public double getActualSellingPrice() 
    {
        return actualSellingPrice;
    }

    //Desc: allows class to set value of the actualSellingPrice field in record
    //Post: actualSellingPrice is set to s
    public void setActualSellingPrice(Double s)
    {
        actualSellingPrice=s;
    }
	
    //Desc:Updates the current record to a new dateOfSale field
    //Post: dateOfSale field is updated
    public void updateDateOfSale()  
    {
        System.out.println("Old Date Of Sale:" + dateOfSale);
        System.out.println("Please enter new Date Of Sale and press <ENTER>: \n");
        Date dos=new Date(UserInterface.getString());
        dateOfSale=dos;
    }

    //Desc: Updates the current record to a new nameOfBuyer field
    //Post: nameOfBuyer field is updated
    public void updateNameOfBuyer()
    {
        System.out.println("Old Name of Buyer:" + nameOfBuyer);
        System.out.println("Please enter new Name of Buyer and press <ENTER>: \n");
        nameOfBuyer=UserInterface.getString();
    }

    //Desc: Updates the current record to a new addressOfBuyer field
    //Post: addressOfBuyer field is updated
    public void updateAddressOfBuyer()
    {
        System.out.println("Old Address of Buyer:" + addressOfBuyer);
        System.out.println("Please enter new Address of Buyer and press <ENTER>: \n");
        addressOfBuyer=UserInterface.getString();
    }

    //Desc: Updates the current record to a new actualSellingPrice field
    //Post: actualSellingPrice field is updated
    public void updateActualSellingPrice()
    {
        System.out.println("Old Actual Selling Price:" + actualSellingPrice);
        System.out.println("Please enter new actualSellingPrice");
        double tempprice=new Double(UserInterface.getString());
        actualSellingPrice=tempprice;

    }
    
    //Desc: uses the last name of an artist and the title of work to find the
    // 		 Bought Painting record
    //Return: returns true if painting record is found, false if not
    
    public boolean find(String alastname, String title)
    {
        try
        {
            File paintingsFile = new File ("GalleryPaintings.dat");
            boolean found = false;
            if (paintingsFile.exists())
            {
                RandomAccessFile inFile = new RandomAccessFile (paintingsFile, "r");
                while (!found && (inFile.getFilePointer()!=inFile.length()))
                {
                    read (inFile);
                    if (artistLastName.equalsIgnoreCase(alastname) && 
                    titleOfWork.equalsIgnoreCase(title))
                        found = true;       
                }
                inFile.close();
            }
            return found;
        }
        catch (Exception e)
        {
            System.out.println ("***** Error: Investment.find () *****");
            System.out.println ("\t" + e);
            return false;
        }
    }

    //Desc: reads a file into the scanner, sets each field in the text file to 
    //		a field in a new Bought Painting object
    //Pre: file must exist
    public void read(RandomAccessFile fileName)
    {
        try
        {
            String  inputString = new String ();	// for storing artist record
            int	i = 0;		                // position in record
            inputString = fileName.readLine ();
            StringBuffer input = new StringBuffer ();	// for storing field within record
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            artistFirstName = input.toString ();
            i++;

            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            artistLastName = input.toString ();
            i++;

            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
             titleOfWork = input.toString ();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++; 
            }
             Date tempdow = new Date (input.toString ());
             dateOfWork = tempdow;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
             classification = input.toString ();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double tempheight = new Double (input.toString ());
            height = tempheight;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double tempwidth = new Double (input.toString ());
            height = tempwidth;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            medium = input.toString();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            subject = input.toString();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double tempmax = new Double (input.toString ());
            suggestedMaximumPurchasePrice = tempmax;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Date tempdop = new Date (input.toString ());
            dateOfPurchase = tempdop;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            nameOfSeller = input.toString();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            addressOfSeller = input.toString();
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double tempactual = new Double (input.toString ());
            actualPurchasePrice = tempactual;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double temptarget = new Double (input.toString ());
            targetSellingPrice = temptarget;
            i++;
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Date tempdos = new Date (input.toString ());
            dateOfSale = tempdos;
            i++; 
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            nameOfBuyer = input.toString();
            i++; 
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            addressOfBuyer = input.toString();
            i++;        
            
            input = new StringBuffer ();
            while (inputString.charAt (i) != '|')
            {
              input.append (inputString.charAt (i));
              i++;
            }
            Double tempactualsell = new Double (input.toString ());
            actualSellingPrice = tempactualsell;
            i++;             
   
        }
        catch (Exception e)
        {
            System.out.println ("***** Error: Arist.read () *****");
            System.out.println ("\t" + e);
        }
    }
	
     	public void write(RandomAccessFile fileName)
        {
            try
            {
                fileName.writeBytes(artistFirstName + "|");
                fileName.writeBytes(artistLastName + "|");
                fileName.writeBytes(titleOfWork + "|");
                fileName.writeBytes(dateOfWork + "|");
                fileName.writeBytes(classification + "|");
                fileName.writeBytes(height + "|");
                fileName.writeBytes(width + "|");
                fileName.writeBytes(medium + "|");
                fileName.writeBytes(subject + "|");
                fileName.writeBytes(suggestedMaximumPurchasePrice + "|");
                fileName.writeBytes(dateOfPurchase + "|");
                fileName.writeBytes(nameOfSeller + "|");
                fileName.writeBytes(addressOfSeller + "|");
                fileName.writeBytes(actualPurchasePrice + "|");
                fileName.writeBytes(targetSellingPrice + "|");
                fileName.writeBytes(dateOfSale + "|");
                fileName.writeBytes(nameOfBuyer + "|");
                fileName.writeBytes(addressOfBuyer + "|");
                fileName.writeBytes(actualSellingPrice + "|"+"\n");
                //double check that this writes doubles, ints, and dates correctly
            }
            catch (IOException e)
            {
                System.out.println ("***** Error: SoldPainting.write () *****");
                System.out.println ("\t" + e);
            }
        }
    
    //Desc: writes the record back to the text file and prompts 
    //      the user the data has been saved
    //Post: changes the text file
   public void save()
    {
        try
        {
            File paintingsFile = new File ("GalleryPaintings.dat");	
            File  tempPaintingsFile = new File ("GalleryPaintings.tmp");	
            BoughtPainting tempPainting = new BoughtPainting ();	
            boolean found = false;		
            RandomAccessFile newFile = new RandomAccessFile (tempPaintingsFile, "rw");

            if (!paintingsFile.exists ())
            {
              write(newFile);
            }
            else
            {
                RandomAccessFile oldFile = new RandomAccessFile (paintingsFile, "r");
                boolean comparePaintings;
                while (oldFile.getFilePointer () != oldFile.length ()) 
                {
                    tempPainting.read(oldFile);
                    if (artistLastName.equalsIgnoreCase(tempPainting.getArtistsLastName()) &&
                    titleOfWork.equalsIgnoreCase(tempPainting.getTitleofWork()))
                        comparePaintings=true;
                    else comparePaintings=false;
                    if(comparePaintings) 
                    {
                        write (newFile); 
                        found=true;
                    } 
                    else
                    {
                      tempPainting.write(newFile); 
                    }
                }  
                if (!found) write (newFile); 

              oldFile.close ();

            }

            newFile.close ();

            paintingsFile.delete ();
            tempPaintingsFile.renameTo (paintingsFile);
            System.out.println("record saved to file");

          }
          catch (Exception e)
          {
              System.out.println ("***** Error: SoldPainting.putRecord () *****");
              System.out.println ("\t" + e);
          }
      }
    
    
    public void performDeletion()
    {
        //need to write this!!!
    }
    
    public void readInRecord()
    {
        //grab this from the UI class!
    }
    
    public void print ()
    {
      System.out.print ("Artist First Name: " + artistFirstName);
      System.out.print ("\t Artist Last Name: " + artistLastName);
      System.out.print ("\t Title Of Work: " + titleOfWork);
      System.out.print ("\t Date Of Work: " + dateOfWork);
      System.out.print ("\t Classification: " + classification);
      System.out.print ("\t Height: " + height);
      System.out.print ("\t Width: " + width);
      System.out.print ("\t Medium: " + medium);
      System.out.print ("\t Subject: " + subject);
      System.out.print ("\t Suggested Max Purchase Price: " + suggestedMaximumPurchasePrice);
      System.out.print ("\t Date Of Purchase: " + dateOfPurchase);
      System.out.print ("\t Name Of Seller: " + nameOfSeller);    
      System.out.print ("\t Address Of Seller: " + addressOfSeller);    
      System.out.print ("\t Actual Purchase Price: " + actualPurchasePrice); 
      System.out.print ("\t Target Selling Price: " + targetSellingPrice);  
      System.out.print ("\t Date of Sale: " + dateOfSale); 
      System.out.print ("\t Name of Buyer: " + nameOfBuyer); 
      System.out.print ("\t Address of Buyer: " + addressOfBuyer); 
      System.out.print ("\t Actual Selling Price: " + actualSellingPrice); 
    } 
}
