Will use Parallel Saga approcach - async with eventual consistency and orchestration

***Ride States***

Happy Path:
1. RideRequested - passenger use mobile app to book a ride
2. RideFraudChecked - fraud service checked for fraud
3. RideRouteFound - geo service found route for a ride
3. RidePriceCalculated - price service calculated price for a ride
4. RideDriverRequested - request to find driver was send to driver service
5. RideDriverSelected - driver was assigned on a ride
6. RideDriverOnPlace - driver arrived in pick-up point
7. RideStarted - passenger in a car and driver started to move
8. RideCompleted - passenger arrived in a place

Financial states:
9. PaymentPending - payment requested
10. PaymentCompleted - payment was processed
11. PayoutRequested - payout requested for driver
12. PayoutCompleted - payout provided to driver


Failures:

1. RideCancelled - passenger cancel ride before driver assigned. (no need to do anything)
2. RideDriverCancelled - passenger cancel drive after driver was assigned 
    - Compensation steps: 
      - Price service calculates compensation fee -> FeeCalculated
      - Payment service requests compensation fee from passenger -> CompensationFeeRequested
      - Payment service completes compensation fee from passenger -> CompensationFeeCompleted
      
3. RideCancelledByDriver - driver cancels ride after was assigned but before arriving to point
    - Compensation steps:
      - Price service calculates fine for driver -> FineCalculated 
      - Payout service collect fine from driver account -> FineRequested
      - Payout service collected fine -> FineCompleted

4. RideFraudDetected - fraud service detected fraud before ride was started
   - Compensation steps:
     - Passenger service will block user -> RideCancelled
   
5. RidePaymentRejected - payment rejected by bank after several attempts
   - Compensation steps:
     - Passenger service will block user
     - PayoutService will request payout for driver -> PayoutRequested
     - PayoutCompleted -> payout provided to driver
     
6. PayoutRejected - unable to complete payout step for some time
    - Compensation steps:
      - include in report for accountant