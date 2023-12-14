import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.RepeatedTest;
import org.junit.jupiter.api.RepetitionInfo;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;

/**
 * TEsts the Triangle class
 * 
 * @author mdixon
 *
 */
class TriangleTest {

	@BeforeAll
	static void setUpBeforeClass() throws Exception {
		
		// nothing to do (could remove)
	}

	@AfterAll
	static void tearDownAfterClass() throws Exception {
		
		// nothing to do (could remove)
	}

	
	@Test
	void defaultConstructor() {
		
		Triangle tri = new Triangle();
		
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
	}
	
	@Test
	void equalConstructor() {
		
		Triangle tri = new Triangle(10);
		
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
	}
	
	@Test
	void multiConstructor() {
		
		Triangle tri = new Triangle(10,10,10);
		
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		tri = new Triangle(10,10,20);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		tri = new Triangle(10,20,30);
		
		assertFalse(tri.isEquilateral());
		assertTrue(tri.isScalene());
		assertFalse(tri.isIsosceles());
	}

	@Test
	void testisScalene() {
		
		Triangle tri = new Triangle(1, 2, 3);
		
		assertFalse(tri.isEquilateral());
		assertTrue(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		// try same arguments, in different order (causes more paths to be covered).
		tri = new Triangle(3, 2, 1);
		
		assertFalse(tri.isEquilateral());
		assertTrue(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		// try same arguments, in different order (causes more paths to be covered).
		tri = new Triangle(2, 3, 1);
		
		assertFalse(tri.isEquilateral());
		assertTrue(tri.isScalene());
		assertFalse(tri.isIsosceles());
	}
	
	@Test
	void testisIsosceles() {
		
		Triangle tri = new Triangle(2, 2, 3);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		// try same arguments, in different order (causes more paths to be covered).
		tri = new Triangle(3, 2, 3);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		// try same arguments, in different order (causes more paths to be covered).
		tri = new Triangle(3, 2, 2);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
	}
	
	@Test
	void testSetAllSides() {
		
		Triangle tri = new Triangle();
		
		tri.setSides(10, 20, 30);
				
		assertFalse(tri.isEquilateral());
		assertTrue(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		tri.setSides(10, 10, 10);
		
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		tri.setSides(20, 20, 30);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		tri.setSides(20, -20, 30);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		tri.setSides(20, 20, -30);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
	}
	
	@Test
	void testSetTwoSides() {
		
		Triangle tri = new Triangle();
		
		tri.setSides(20, 30);
				
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		tri.setSides(90, 1);
		
		assertFalse(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertTrue(tri.isIsosceles());
		
		tri.setSides(10, 10);
		
		assertFalse(tri.isEquilateral());	// FAILS: showing comment on code is wrong!
		assertFalse(tri.isScalene());	
		assertTrue(tri.isIsosceles());		// FAILS: showing comment on code is wrong!
	}
	
	@Test
	void testSetOneSide() {
		
		Triangle tri = new Triangle();
		
		tri.setSides(10);
				
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		tri.setSides(-10);
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
	}
	
	@Test
	void testCopy() {
		
		Triangle tri = new Triangle();
		
		Triangle tri2 = tri.copy();
		
		// change sides of copy
		tri2.setSides(10, 20, 30);
				
		// should not effect original
		assertTrue(tri.isEquilateral());
		assertFalse(tri.isScalene());
		assertFalse(tri.isIsosceles());
		
		assertFalse(tri2.isEquilateral());
		assertTrue(tri2.isScalene());
		assertFalse(tri2.isIsosceles());
	}
	
	
	@ParameterizedTest
	@CsvSource({ "1,1,1", "1,2,3", "10,10,20", "15, 16, 15", "3,2,1", "100,100,100", "20, 21, 21", "1,1000,2" })
	void testPerimeter(int sideA, int sideB, int sideC) {
		
		// uses each set of CSV specified triplet values
		Triangle tri = new Triangle(sideA, sideB, sideC);
		
		// FAILS: identifies bug within getPerimeter()
		assertEquals(sideA + sideB + sideC, tri.getPerimeter());
	}
	
	@RepeatedTest(5)
	void testAveLength(RepetitionInfo repetitionInfo) {
		
		int repCount = repetitionInfo.getCurrentRepetition();
		
		// uses value from each repetition
		Triangle tri = new Triangle(repCount, repCount * 2, repCount * 3);
		
		// FAILS: identifies bug within getAverageLength()
		assertEquals((repCount + repCount * 2 + repCount * 3)/3, tri.getAverageLength());
	}
	
	@Test
	void breakgetPerimeter() {
		
		Triangle tri = new Triangle(2000000000, 2000000000, 2000000000);
		
		assertEquals(6000000000L, tri.getPerimeter()); 	// FAILS: overflows max size of return type 'int'
														// Could fix by returning long value from getPerimeter()
	}
}
