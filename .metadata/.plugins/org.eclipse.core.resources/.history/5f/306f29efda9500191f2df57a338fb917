package parking_calculator;
import static org.assertj.core.api.Assertions.assertThat;
import java.io.FileReader;
import java.io.IOException;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.PageFactory;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.DataProvider;
import org.testng.annotations.Test;
import com.opencsv.CSVReader;
import java.util.List;
import java.util.Objects;

public class ShortTermParking {

	private WebDriver driver;
	PageObjects pageObjects;
	CSVReader csvReader;
	// csv file location
	private static final String SAMPLE_CSV_FILE_PATH = "C:\\Users\\ahoss1\\Desktop\\Parking_Calculator\\parking_calculator\\csvfile\\short_term_parking.csv";

	@SuppressWarnings("deprecation")
	@BeforeClass
	public void beforeTest() throws IOException {
		String path = System.getProperty("user.dir");
		// Reader reader = Files.newBufferedReader(Paths.get(SAMPLE_CSV_FILE_PATH));
		// csvReader = new CSVReader(reader);

		// OpenCSV Library: Skipping column header from csv file
		csvReader = new CSVReader(new FileReader(SAMPLE_CSV_FILE_PATH), ',', '"', 1);

		// Chromedriver location
		System.setProperty("webdriver.chrome.driver", path + "\\chromedriver\\chromedriver.exe");

		// Create a new instance of the Chrome driver
		driver = new ChromeDriver();

		// Launch the URL
		driver.navigate().to("http://adam.goucher.ca/parkcalc");

		// This is to Instantiate Page Objects class
		pageObjects = PageFactory.initElements(driver, PageObjects.class);

	}

	@Test(dataProvider = "getData")

	public void shortTermParking(String EntryDate, String EntryTime, String LeavingDate, String LeavingTime,
			String ExpectedCost) throws InterruptedException {
		pageObjects.EntryTime(EntryTime); // Entering EntryTime from csv
		pageObjects.EntryDate(EntryDate); // Entering EntryDate from csv
		pageObjects.ExitTime(LeavingTime); // Entering LeavingTime from csv
		pageObjects.ExitDate(LeavingDate); // Entering LeavingDate from csv
		pageObjects.Calculate();

		// Get estimated cost from the screen
		String ActualCost = pageObjects.GetText();
		//System.out.println(pageObjects.GetText());
		// Verify the cost using AssertJ: "ExpectedCost" is pre-calculated in csv file
		// where "ActualCost" is taken from the screen
		assertThat(ActualCost).isEqualTo(ExpectedCost);
	}

	@DataProvider(name = "getData")
	public Object[][] getData() throws Exception {
		// Reading from csv
		List<String[]> records = csvReader.readAll();

		Object[][] array = null;

		for (int i = 0; i < records.size(); i++) {

			Object[] row = records.get(i);
			if (Objects.isNull(array)) {
				array = new Object[records.size()][row.length];
			}
			//
			array[i][0] = row[0];
			array[i][1] = row[1];
			array[i][2] = row[2];
			array[i][3] = row[3];
			array[i][4] = row[4];
		}
		return array;
	}

	@AfterClass
	public void afterTest() {
		// Kill the browser
		driver.quit();
	}
}
