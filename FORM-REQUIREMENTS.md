# Front End Design Elective - Spring 2020

## System 1, the booking site, requirements

The following are the minimal requirements for the booking site.

- The site should be a "form flow" where the user can buy multiple tickets.

  - ticket prizes
    - Regular 799,-
    - VIP 1299,-

- During the purchase, the user can choose to prebook a camping spot.
  - Base price 99,-
  - Optional "Green camping option +249,-"
  - Optional, pay to have the crew set up X tents for you.
    - 2 person tent (including the tent) 299,-
    - 3 person tent (including the tent) 399,-
    - The number to tents must match the number of people in the group (number of tickets).
- The flow should contain everything you would expect from an online shopping experience, like personal info, checkout, etc.
- We need the personal info for the owner of each ticket.
- Content from the form (except payment info) should be stored in a database. That database is not provided by the API
- The site it self will be the landing page of our festival, so make it awesome. We do not yet have a logo or a visual identity, go crazy

You are free to add other features.

### Using the API

The endpoint `/available-spots` will give you a list of available camping spots that can be booked, including how many spots are left.

Once the user has chosen an area, the system must send a `PUT` request to the endpoint `/reserve-spot` with the following payload:

```
{
	"area":"Alfheim",
	"amount":3
}
```

This will return an id for the reservation. The reservation is valid for 5 minutes. To confirm the reservation, the system must send a `POST` request to the endpoint `/fullfill-reservation` with the following payload:

```
{
	"id":"sktwi6kwl1d9e787"
}
```

using the id from the previous request

## Payment

Fake it, but make sure that the form has validation and a nice UX
