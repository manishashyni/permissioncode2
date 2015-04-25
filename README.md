# permissioncode2
package try11;
import java.io.File;
import java.io.IOException;

public class FolderCreation {

	public static void main(String args[]) throws IOException {
        boolean success = false;
       // boolean s;
    
      Runtime.getRuntime().exec("net use p: \\\\ad.infosys.com\\storage\\gec\\TRAINEE\\HANDSON\\Sandeep_forToolTesting");
     
      File f = new File("p:\\xy4"); 
      {
  if (f.exists()) {
      System.out.println("File already exists");

  } else {
      System.out.println("No such file exists, creating now");
     
			success = f.mkdir();
			System.out.println(success);
		//	Runtime.getRuntime().exec("icacls p:\\xy4 /deny Everyone:W");
		//	Runtime.getRuntime().exec("icacls p:\\xy4 /grant :r Gonugunta Manisha Shyni(523479)(Gonugunta_523479@ad.infosys.com):(OI)(CI)F /grant :r Everyone:(OI)(CI)R");
		
			// Take ownership of the folder.
			Runtime.getRuntime().exec("TAKEOWN /f p:\\xy4 /r /d y");
			// Clear folder permissions.
			Runtime.getRuntime().exec("ICACLS p:\\xy4 /reset /T");
			
			// Only allow Shyni to have full control and everyone else to read.
			Runtime.getRuntime().exec("icacls p:\\xy4 /grant :r Gonugunta Manisha Shyni(523479)(Gonugunta_523479@ad.infosys.com):(OI)(CI)F /grant :r Everyone:(OI)(CI)R");
			// Set inheritance on everythin below.
			Runtime.getRuntime().exec("icacls p:\\xy4 /inheritance:r);
		}
      if (success) {
          System.out.printf("Successfully created new file: %s%n", f);
      } else {
          System.out.printf("Failed to create new file: %s%n", f);
      }
      }
	}
}

        
