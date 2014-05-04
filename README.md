SoldPainting
============
package artpricingsystem;

import java.io.File;
import java.io.RandomAccessFile;
import java.util.Date;
import java.util.Scanner;

/**
 *
 * @author jessicaspalding
 */
public class SoldPainting extends BoughtPainting
{
    private Date dateOfSale;
    private String nameOfBuyer;
    private String addressOfBuyer;
    private double actualSellingPrice; 

    //Desc: constructor for BoughtPainting
    //Post: allow class to set the value of all Bought Painting fields in a record
    /*SoldPainting(String fname, String lname, String work, Date dwork, 
    String clas, double h, double w, String med, String sub, double max, 
    Date d, String n, String a, double p, double t)
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
        suggestedMaxPurchPrice=max;
        dateOfPurchase=d;
        nameOfSeller=n;
        addressOfSeller=a;
        actualPurchasePrice=p;
        targetSellingPrice=t;
    } */
    
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
        suggestedMaxPurchPrice=max;
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
    public void updateDateOfSale()  //need to fix
    {
        System.out.println("Old Date Of Sale:" + dateOfSale);
        System.out.println("Please enter new Date Of Sale");
        Scanner input=new Scanner(System.in);
        Date tempdos = new Date (input.toString ());
        dateOfSale=tempdos;
    }

    //Desc: Updates the current record to a new nameOfBuyer field
    //Post: nameOfBuyer field is updated
    public void updateNameOfBuyer()
    {
        System.out.println("Old Name of Buyer:" + nameOfBuyer);
        System.out.println("Please enter new Name of Buyer");
        Scanner input=new Scanner(System.in);
        nameOfBuyer=input.toString();
    }

    //Desc: Updates the current record to a new addressOfBuyer field
    //Post: addressOfBuyer field is updated
    public void updateAddressOfBuyer()
    {
        System.out.println("Old Address of Buyer:" + addressOfBuyer);
        System.out.println("Please enter new Address of Buyer");
        Scanner input=new Scanner(System.in);
        addressOfBuyer=input.toString();
    }

    //Desc: Updates the current record to a new actualSellingPrice field
    //Post: actualSellingPrice field is updated
    public void updateActualSellingPrice()
    {
        System.out.println("Old Actual Selling Price:" + actualSellingPrice);
        System.out.println("Please enter new actualSellingPrice");
        Scanner input=new Scanner(System.in);
        Double tempactual = new Double (input.toString ());
        actualSellingPrice=tempactual;

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
            suggestedMaxPurchPrice = tempmax;
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
        /*    private Date dateOfSale;
    private String nameOfBuyer;
    private String addressOfBuyer;
    private double actualSellingPrice; */
        catch (Exception e)
        {
            System.out.println ("***** Error: Arist.read () *****");
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
            File paintingsFile = new File ("GalleryPaintings.dat");	// file of artist
            File  temppaintingsFile = new File ("GalleryPaintings.tmp");	// temporary file for artist

            SoldPainting tempSoldPainting = new SoldPainting();	// record read, then written
            boolean found = false;		// terminates while-loop

            RandomAccessFile newFile = new RandomAccessFile (temppaintingsFile, "rw");

            if (!paintingsFile.exists ())
            {
              write(newFile);
            }
            else
            {
                RandomAccessFile oldFile = new RandomAccessFile (paintingsFile, "r");

                int comparePaintings; // to find correct place for the new investment

                while (oldFile.getFilePointer () != oldFile.length ()) //the pointer hasn't reached the end of the file
                {
                    tempSoldPainting.read(oldFile); //read walks through each field in the record

                    if (artistLastName.equals(tempSoldPainting.getArtistLastName())
                        && titleOfWork.equals(tempSoldPainting.getTitleofWork()))
                        comparePaintings=1;
                    else comparePaintings=0;

                    if (comparePaintings ==1) 
                    {
                        write (newFile); //replaces old file record with new file record
                    } 
                    else
                    {
                      tempSoldPainting.write (newFile); //writes to 2nd temp file
                    }
              }  // while

              //if (compareArist==0) write (newFile); // if never found in file, write to temp file

              oldFile.close ();

            }  // else

            newFile.close ();

            paintingsFile.delete ();
            temppaintingsFile.renameTo (paintingsFile);
            System.out.println("record saved");

          }
          catch (Exception e)
          {
              System.out.println ("***** Error: Artist.putRecord () *****");
              System.out.println ("\t" + e);
          }
    }
    
}
