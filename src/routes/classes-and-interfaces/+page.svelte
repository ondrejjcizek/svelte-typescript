<script lang="ts">
    class Department {
        // private readonly id: string;
        // private name: string;
        protected employees: string[] = []

        constructor(private readonly id: string, public name: string) {
            // this.id = id;
            // this.name = n;
        }

        describe(this: Department) {
            console.log(`Department (${this.id}): ${this.name}`);
        }

        addEmployee(employee: string): void {
            // this.id = 'd2'; // its a readonly property
            this.employees.push(employee);
        }

        printEmployeeInformation() {
            console.log(this.employees.length);
            console.log(this.employees);
        }
    }

    class ITDepartment extends Department {
        constructor(id: string, public admins: string[]) {
            super(id, 'IT');
        }
    }

    class AccountingDepartment extends Department {
        constructor(id: string, private reports: string[]) {
            super(id, 'IT');
        }

        addEmployee(name: string) {
            if (name === 'Max') {
                return;
            }
            this.employees.push(name);
        }

        addReport(text: string) {
            this.reports.push(text);
        }

        printReports() {
            console.log(this.reports)
        }
    }

    const it = new ITDepartment('d1', ['Max']);

    it.addEmployee('Max')
    it.addEmployee('Manu')

    // it.employees[2] = 'Anna' // not working bacause its private

    it.describe();
    it.printEmployeeInformation();

    console.log(it)

    const accounting = new AccountingDepartment('d2', []);

    accounting.addReport('Something went wrong...')

    accounting.addEmployee('Max')
    accounting.addEmployee('Manu')

    accounting.printReports()
    accounting.printEmployeeInformation();

    // const accountingCopy = { name: 'DUMMY', describe: accounting.describe };
    // accountingCopy.describe(); // not working bacause there are not filled all the properties

</script>

<h5>Classes and Interfaces</h5>