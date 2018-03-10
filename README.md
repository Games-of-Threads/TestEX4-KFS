# TestEX4-KFS
> by Kristian FLejsborg Sørensen (cph-kf96)

## Code

Hamcrest test cases
```
@org.junit.jupiter.api.Test
    void createPolygon() throws Exception {
        PolygonHandler PH = new PolygonHandlerImpl();
        double[] sides = {1,1,1};
        Polygon a = PH.CreatePolygon(sides);
        String b = Double.toString(a.sides[0])+Double.toString(a.sides[1])+Double.toString(a.sides[2]);
        assertThat(b, anyOf(is("1.01.01.0")));
    }

    @org.junit.jupiter.api.Test
    void comparePolygonByPerimeter() throws Exception {
        PolygonHandler PH = new PolygonHandlerImpl();
        double[] sides = {3,3,3};
        Polygon a = PH.CreatePolygon(sides);
        sides = new double[]{4,3,3};
        Polygon b = PH.CreatePolygon(sides);
        Polygon Best = PH.ComparePolygonByPerimeter(a,b);
        assertThat(b.toString(), anyOf(is(Best.toString())));
    }
```
Data Driven Test cases
```
    @Test
    void DataDrivenTest1() throws Exception {
        ObjectMapper mapper = new ObjectMapper();
        ArrayList<Polygon> list = new ArrayList<Polygon>();
        Polygon[] mypolygonArray = mapper.readValue(new File("C:\\output\\mylist.json"), Polygon[].class);
        for (Polygon polygon : mypolygonArray) {
            list.add(polygon);
        }
        PolygonHandler PH = new PolygonHandlerImpl();
        list = PH.SortByArea(list);
        list.forEach(x -> System.out.println(x.sides[0]+x.sides[1]+x.sides[2]));
    }

    @Test
    void DataDrivenTest2() throws Exception {
        ObjectMapper mapper = new ObjectMapper();
        ArrayList<Polygon> list = new ArrayList<Polygon>();
        Polygon[] mypolygonArray = mapper.readValue(new File("C:\\output\\mylist.json"), Polygon[].class);
        for (Polygon polygon : mypolygonArray) {
            list.add(polygon);
        }
        PolygonHandler PH = new PolygonHandlerImpl();
        list = PH.SortByPerimeter(list);
        list.forEach(x -> System.out.println(x.sides[0]+x.sides[1]+x.sides[2]));
    }
```

![](https://i.gyazo.com/21143c3be1d85e284b8b6a749c5049fb.png)
