# LEETCODE-Array-729
Let's walk through a dry run of your `MyCalendar` class with a sequence of bookings. Here’s the code again for context:

```java
class MyCalendar {
  public boolean book(int start, int end) {
    for (int[] t : timeline)
      if (Math.max(t[0], start) < Math.min(t[1], end))
        return false;
    timeline.add(new int[] {start, end});
    return true;
  }

  private List<int[]> timeline = new ArrayList<>();
}
```

### Dry Run Example

Let's assume the following sequence of bookings:

- Booking 1: `(10, 20)`
- Booking 2: `(15, 25)`
- Booking 3: `(20, 30)`

#### Booking 1: `book(10, 20)`
1. The timeline is empty at the start.
2. Since there are no previous bookings, the loop over `timeline` doesn't run.
3. The time interval `[10, 20]` is added to `timeline`.
4. The method returns `true` because the booking was successful.

Timeline: `[[10, 20]]`

#### Booking 2: `book(15, 25)`
1. The timeline now contains one interval: `[[10, 20]]`.
2. Looping over the timeline:
   - For the interval `[10, 20]`:
     - Calculate `Math.max(10, 15)` = `15`.
     - Calculate `Math.min(20, 25)` = `20`.
     - Since `15 < 20`, there is an overlap, and the method returns `false`.
3. The booking fails because it conflicts with an existing booking.

Timeline: `[[10, 20]]`

#### Booking 3: `book(20, 30)`
1. The timeline contains `[[10, 20]]`.
2. Looping over the timeline:
   - For the interval `[10, 20]`:
     - Calculate `Math.max(10, 20)` = `20`.
     - Calculate `Math.min(20, 30)` = `20`.
     - Since `20 == 20`, there is no overlap (no time is shared).
3. The interval `[20, 30]` is added to `timeline`.
4. The method returns `true` because the booking was successful.

Timeline: `[[10, 20], [20, 30]]`

### Final State

- Timeline after all bookings: `[[10, 20], [20, 30]]`
- Booking results: `true`, `false`, `true`

This demonstrates how the `MyCalendar` class prevents overlaps in the booked intervals and only allows non-overlapping bookings.
