import java.util.Scanner;

// Calculate the distance between two Longitude / Latitude points on an Earth-sized sphere.
// Compare results with https://www.nhc.noaa.gov/gccalc.shtml
// Note inputs are (Longitude, Latitude) decimal format.
public class DistanceCalculator {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		LatLongPair in = new LatLongPair(input.nextDouble(), input.nextDouble());
		LatLongPair in2 = new LatLongPair(input.nextDouble(), input.nextDouble());
		System.out.println(in + " " + in.toPoint3D());
		System.out.println(in2 + " " + in2.toPoint3D());
		System.out.println(in.getDistance(in2));
		
	}
	
	public static class Point3D {
		double x;
		double y;
		double z;
		Point3D(double _x, double _y, double _z) {
			x = _x;
			y = _y;
			z = _z;
		}
		
		public double difference(Point3D other) {
			return Math.sqrt((x-other.x)*(x-other.x) + (y-other.y)*(y-other.y) + (z-other.z)*(z-other.z));
		}
		
		public String toString() {
			return "(" + x + ", " + y + ", " + z + ")";
		}
	}
	
    public static class LatLongPair {
    	double latitude;
    	double longitude;
    	static double radius = 3958.8;
    	public LatLongPair(double _longitude, double _latitude) {
    		longitude = _longitude / 180 * Math.PI;
    		latitude = _latitude / 180 * Math.PI;
    	}
    	
    	public Point3D toPoint3D() {
    		double x = radius * Math.sin(longitude) * Math.cos(latitude);
    		double y = radius * Math.cos(longitude) * Math.cos(latitude);
    		double z = radius * Math.sin(latitude);
    		return new Point3D(x,y,z);
    	}   	
    	
    	public double getDistance(LatLongPair other) {
    		Point3D first = this.toPoint3D();
		    Point3D second = other.toPoint3D();
    		
    		double dist = first.difference(second);
    		double angle = Math.acos((dist * dist - radius * radius - radius * radius) / (-2 * radius * radius));
    		    	
    		return radius * angle;
    	}
    	
    	public String toString() {
    		return (longitude + " " + latitude);
    	}
    }
}
