# python-waterbill
customer_code = raw_input("Please enter the Customer Code")
beginning_meter = float (raw_input("Please enter your beginning meter reading here: "))
ending_meter = float (raw_input("Please enter your ending meter reading here: "))

def waterUsage (a,b):
	result = float(b)-float(a)
	if result > 0:
		return result 
	else:
		result = (999999999-a)+b
		return result 	

gallons = waterUsage(beginning_meter,ending_meter)

if customer_code == "r":
	def amountBilled():
		result = 5+(float(gallons)*.0005)
		return result
		
elif customer_code == "c":
	def amountBilled():
		if gallons < 4000000:
			result = 10000
			return result
		else: 
			result = 10000+((float(gallons)-4000000)*.00025)
			return result

elif customer_code == "i":
	def amountBilled():
		if gallons < 4000000:
			result = 1000
			return result
		elif gallons >= 4000000 and gallons <= 10000000:
			result = 2000
			return result
		else:
			result = 2000 +((float(gallons)-10000000)*.00025)
			return result


#Customer Code:
#Beginning Meter Reading: 
#Ending Meter Reading:
#Gallons of water used:
#Amount Billed: 

print "Customer Code: {0}\nBeginning Meter Reading: {1}\nEnding Meter Reading: {2}\nGallons of water used: {3}\nAmount Billed: ${4}".format(customer_code,beginning_meter,ending_meter,gallons,amountBilled())
