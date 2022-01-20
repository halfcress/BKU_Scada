from opcua import Client
import time
import datetime

def get_zone_temp_pv(zone_number):
     for index in range(0,zone_number):
            var = client.get_node("ns=3;s= \"TEMP_CTRL_DB\".\"ZONE_CTRL\"["+str(index)+"].\"PV\" ")
            print("Zone{i} PV is {value}".format(i=index+1,value=var.get_value()))
            time.sleep(0.1) 
def get_zone_temp_sp(zone_number):
    for index in range(0,zone_number):
            var = client.get_node("ns=3;s= \"TEMP_CTRL_DB\".\"ZONE_CTRL\"["+str(index)+"].\"SP\" ")
            print("Zone{i} SP is {value}".format(i=index+1,value=var.get_value()))
            time.sleep(0.1) 
def get_quench_height_pv():
    var = client.get_node("ns=3;s= \"AUTO_QUENCH_HEIGHT_DB\".\"Scaled_Quench_Height\" ")
    print("Quench yüksekligi :{height}".format( height=var.get_value()/10 ))
def get_quench_height_sp():
    var = client.get_node("ns=3;s= \"AUTO_QUENCH_HEIGHT_DB\".\"Quench_Height_SP\" ")
    print("Cam recete kalinligi:{thickness}".format( thickness=var.get_value()/10 ))
def get_quench_speed():
    var = client.get_node("ns=3;s= \"DRIVE_QUENCH\".\"CURRENT_DRIVE_SPEED_SP\" ")
    print("Quench hizi:{qspeed} ipm".format(qspeed=var.get_value()))
def get_oven_speed():
    var = client.get_node("ns=3;s= \"DRIVE_OVEN\".\"CURRENT_DRIVE_SPEED_SP\" ")
    print("Firin hizi:{ospeed} ipm".format(ospeed=var.get_value()))
def get_so2_perc():
    var = client.get_node("ns=3;s= \"CHF_SO2_DB\".\"On/Off_Duty_Cycle_%\" ")
    print("SO2 Cycle %:{perc}".format(perc=var.get_value()))
def get_cooling_pressure_sp():
    var = client.get_node("ns=3;s= \"QUENCH_COOLING_CONTROL_DB\".\"COOL1_SP\"")
    print("Cooling fan pressure sp:{qpressure}".format(qpressure=var.get_value()/10))
def get_cooling_pressure_pv():
    var = client.get_node("ns=3;s= \"QUENCH_COOLING_CONTROL_DB\".\"COOL1\".\"PV_Scaled\"")
    print("Cooling fan pressure pv:{qpressure}".format(qpressure=var.get_value()/10))
def get_quench_pressure_sp():
    var = client.get_node("ns=3;s= \"QUENCH_COOLING_CONTROL_DB\".\"HP_QUE_SP\"")
    print("Quench fan pressure pv:{qpressure}".format(qpressure=var.get_value()/10))
def get_quench_pressure_pv():
    var = client.get_node("ns=3;s= \"QUENCH_COOLING_CONTROL_DB\".\"HP_QUE\".\"PV_Scaled\"")
    print("Quench fan pressure pv:{qpressure}".format(qpressure=var.get_value()/10))
def init():
    get_zone_temp_pv(12)    
    get_zone_temp_sp(12)
    get_quench_height_pv()
    get_quench_height_sp()
    get_quench_speed()
    get_oven_speed()
    get_so2_perc()
    get_cooling_pressure_sp()
    get_cooling_pressure_pv()
    get_quench_pressure_sp()
    get_quench_pressure_pv()   

if __name__ == "__main__":  
    client = Client("opc.tcp://10.16.230.214:4840") #TGL CHF6350 OpcUa Server
    client.connect()
    print(datetime.datetime.now())
    try:
        init() 
    except IndexError:
        print()
    finally:
        client.disconnect()
