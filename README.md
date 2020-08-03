# Created Finance-Report-Using-SSRS

SQL Query used for this report as follows

SELECT p.FirstName AS 'Current Owner', pro.Bedroom , pro.Bathroom,
a.Number + ' ' + a.Street AS 'Property address:', pe.Amount, pe.Date, pe.Description,prf.Amount AS 'Rental Payment'
FROM Property pro 
INNER JOIN Address a 
ON pro.AddressId = a.AddressId 
INNER JOIN PropertyExpense pe 
ON pe.PropertyId = pro.Id
INNER JOIN [dbo].[PropertyRentalPayment] prf
ON prf.PropertyId = pro.Id
INNER JOIN [dbo].[OwnerProperty] op
ON op.PropertyId = pro.Id
INNER JOIN [dbo].[Person] p
ON p.Id = op.OwnerId
WHERE pro.Name = 'Property A'
